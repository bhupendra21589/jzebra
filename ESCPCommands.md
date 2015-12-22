# Introduction #

<font color='red'>Note:  Commands such as append("\x1B"); have limitations due to the way JavaScript converts certain characters (especially the \x00 NUL character).  This tutorial has not been updated to reflect the appendHex() function.  It's syntax is appendHex("x1B"); For ESC/P, it's recommended to use this method over append() when possible. -Tres</font>

I would like to share my experiences on how to use ESC/P commands with jZebra, especially sending the commands to applet with your server-side scripts as I can see there is not much information neither on the mailing list nor in the web.

The problems we dealt with is mostly the following:

**Unknown ASCII characters. (German, Turkish & other characters)** Very few ESC/P commands working on some older pos printers
**Due to no ESC a commands available in these printers (alignment command), defining and dealing with raw text outputs on fixed-size line widths for mixed-size variables.**

Although I cannot talk about all EPSON POS Printers (nor Star nor Citizen), we mostly tried our outputs on TM-T88, TM-T88II, TM-T70. The most avaible command for these older Printers for styling is "ESC !".

# Details #

```

applet.append("\x1B\x40"); // 1
applet.append("\x1B\x21\x08"); // 2
applet.append(" International \r\n");
applet.append(" Company \r\n");
applet.append("\x1B\x21\x01"); // 3
applet.append(" ************************************************** \r\n");
applet.append("Info: 42972\r\n");
applet.append("Info: Kommm\r\n");
applet.append("Datum: 14:00 01/02\r\n");
applet.append(" -------------------------------------------------- \r\n");
applet.append("Info: 42972\r\n");
applet.append("Info: Kommm\r\n");
applet.append("Datum: 14:00 01/02\r\n");
applet.append(" -------------------------------------------------- \r\n");
applet.append(" \r\n");
applet.append(" \r\n");
applet.append(" \r\n");
applet.append(" \r\n");
applet.append("\x1D\x56\x41"); // 4
applet.append("\x1B\x40"); // 5

```

# Here it starts with initation command ESC @ (hex: \x1B\x40)
# Set style to bold with font A ( bit 0 (indicates font 0) + bit 8 (indicates emphasize) = 8, ESC ! 8, hex: \x1B\x08)
# Set style to font B, without any style (bit 1 = 1, ESC ! 1, hex: \x1B\x01)
# Cut command
# Make sure to reset printer if any other program is using this one, just in case it won't reset it.

The most annoying problem here is, you need to know how much bold characters you can fill in one line. This is why the header has less characters than the information lines.
ESC ! command can be easily found in ESC/P documentations.

## Clean String ##

From PHP to Javascript, sending the hex commands with json\_encode() was ruining the codes and somehow jZebra cannot understand those. Therefore we decided to send them like this.

```
$stringBuilder = 'var $PRINTERFUNCTION = function(applet) { '."\n";
foreach ($this->Output as $line) {
    $stringBuilder .= "\t".'applet.append("' . str_replace(array('"',"\n","\r"),array('\"','\n','\r'),$line) . '");'."\r\n";
}
$stringBuilder .= '}'."\n";
return $stringBuilder; 
```

where we stored every line as plain javascript text (no encoding or anything) as array in $this->Ouput. We only filtered plain text variables but not ESC/P Commands ofc. E.g:

```
$this->Output[] = '\x1B\x08';
$this->Output[] = cleanString('I am bold! ÖÜ'); 
```

We filtered texts with the following php function for ascii safe text not to break printer from working although it might show some strange characters:

```
$GLOBALS['normalizeChars'] = array(
'Š'=>'S', 'š'=>'s', 'Ð'=>'Dj','Ž'=>'Z', 'ž'=>'z', 'À'=>'A', 'Á'=>'A', 'Â'=>'A', 'Ã'=>'A', 'Ä'=>'A',
'Å'=>'A', 'Æ'=>'A', 'Ç'=>'C', 'È'=>'E', 'É'=>'E', 'Ê'=>'E', 'Ë'=>'E', 'Ì'=>'I', 'Í'=>'I', 'Î'=>'I',
'Ï'=>'I', 'Ñ'=>'N', 'Ò'=>'O', 'Ó'=>'O', 'Ô'=>'O', 'Õ'=>'O', 'Ö'=>'O', 'Ø'=>'O', 'Ù'=>'U', 'Ú'=>'U',
'Û'=>'U', 'Ü'=>'U', 'Ý'=>'Y', 'Þ'=>'B', 'ß'=>'Ss','à'=>'a', 'á'=>'a', 'â'=>'a', 'ã'=>'a', 'ä'=>'a',
'å'=>'a', 'æ'=>'a', 'ç'=>'c', 'è'=>'e', 'é'=>'e', 'ê'=>'e', 'ë'=>'e', 'ì'=>'i', 'í'=>'i', 'î'=>'i',
'ï'=>'i', 'ð'=>'o', 'ñ'=>'n', 'ò'=>'o', 'ó'=>'o', 'ô'=>'o', 'õ'=>'o', 'ö'=>'o', 'ø'=>'o', 'ù'=>'u',
'ú'=>'u', 'û'=>'u', 'ý'=>'y', 'ý'=>'y', 'þ'=>'b', 'ÿ'=>'y', 'ƒ'=>'f', 'ı'=>'i', 'İ'=>'I', 'ş'=>'s',
'Ş'=>'S', 'ü'=>'u', 'Ü'=>'U', 'ğ'=>'g', 'Ğ'=>'G', "\r"=>'', "\n"=>''
);
function cleanString (&$string) {
    $string = strtr($string, $GLOBALS['normalizeChars']);
    $string = mb_convert_encoding($string,'ASCII');
} 
```

I also want to share our static EPSON styling php class to see how ESC ! command can be done in action:


```
class EpsonStatic {
    static function Init() {
        return '\x1B\x40';
    }
    static function ResetStyles() {
        return '\x1B\x21\x00';
    }
    static function MakeStyle($font, $bold = false, $underline = false, $double_width = false, $double_height = false) {
        $hex = 0;
        if ($font) {
            $hex += $font;
        }
        if ($bold) {
            $hex += 8;
        }
        if ($underline) {
            $hex += 80;
        }
        if ($double_width) {
            $hex += 20;
        }
        if ($double_height) {
            $hex += 10;
        }
        if ($hex < 10) {
            $hex = '0'.$hex; }
            return '\x1B\x21\x'.$hex;
        }
    static function Cut() {
        return '\x1D\x56\x41';
    }
} 
```

The [directPrint.js](http://code.google.com/p/jzebra/downloads/list?can=2&q=directPrint) in jZebra website is also very useful to see some more styling action for raw text printing, but somehow it was too much for us.

I hope these will help people like us, as there is really not many documentation and howTo's to learn these stuff.

Best Regards
Bahadir