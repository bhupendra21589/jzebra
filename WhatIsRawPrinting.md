## What is Raw Printing? ##
"Raw Printing", "DOS Printing", "Line Mode Printing", or generically any "Page Description Language ([PDL](http://en.wikipedia.org/wiki/Page_description_language))", are all examples of sending a series of characters directly to the printer in the printer's native language.  This is the recommended approach when using jZebra because jZebra is able to bypasses the default print behavior of your web browser and allows you to "program" your own print commands.

## What do Raw Printing Characters Look Like? ##

[![](http://jzebra.googlecode.com/files/zpl_small.png)](http://code.google.com/p/jzebra/wiki/WhatIsRawPrinting#ZPL) [![](http://jzebra.googlecode.com/files/epcl_small.png)](http://code.google.com/p/jzebra/wiki/WhatIsRawPrinting#EPCL) [![](http://jzebra.googlecode.com/files/escp_small.png)](http://code.google.com/p/jzebra/wiki/WhatIsRawPrinting#ESCP)

These characters may be human-readable, such as `"^XA^CF,0,0,0^PR12^MD30^PW800^PON^CI13"` or may be unreadable such as special characters `"CHR(00)"`, `"&H1B"`, `"CHR(27)"`.  In both cases they are a series of commands known as a "Printer Language" that your printer manufacturer specifies.

## What are some common Raw Printing Languages? ##
Some common printer languages are: ESC/P (Epson, Star, Citizen), ZPL (Zebra), EPL/EPCL/CPCL (Eltron/Zebra), Line Mode ("Impact/Dotmatrix", Okidata, IBM), and CPL (Cognitive Printing Language).  Most programmer's guides will offer examples in a programming language such as BASIC.  Translating these commands to JavaScript is necessary in order to use jZebra in your webpage.

## What is Raw Printing Used For? ##
Raw Printing is commonly used for receipt printers, barcode printers, encoding/embossing printers, and for ejecting cash registers.  Many thermal printers accept raw commands as well.

If your organization does any of the above printing, chances are, it's already using Raw Printing and to use these commands in jZebra, you simply need to convert the characters to JavaScript.

If your printer does not support Raw Printing, you will need to use [PostScript](WhatIsPostScriptPrinting.md) printing instead.

<br><br><br><br>
<h2>ZPL</h2>
<table><thead><th> <a href='http://code.google.com/p/jzebra/wiki/WhatIsRawPrinting#What_do_Raw_Printing_Characters_Look_Like?'><img src='http://jzebra.googlecode.com/files/zpl.png' /></a> </th></thead><tbody></tbody></table>


<br><br><br><br>
<h2>EPCL</h2>
<table><thead><th> <a href='http://code.google.com/p/jzebra/wiki/WhatIsRawPrinting#What_do_Raw_Printing_Characters_Look_Like?'><img src='http://jzebra.googlecode.com/files/epcl.png' /></a> </th></thead><tbody></tbody></table>


<br><br><br><br>
<h2>ESCP</h2>
<table><thead><th> <a href='http://code.google.com/p/jzebra/wiki/WhatIsRawPrinting#What_do_Raw_Printing_Characters_Look_Like?'><img src='http://jzebra.googlecode.com/files/escp.png' /></a> </th></thead><tbody></tbody></table>

Article on Page Description Language (PDL):<br>
<a href='http://en.wikipedia.org/wiki/Page_description_language'>http://en.wikipedia.org/wiki/Page_description_language</a>


-Tres