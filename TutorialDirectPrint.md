# Simple Usage of directPrint #

It must be used with [jQuery](http://www.jquery.com/) library.

Attach jQuery and directPrint in your html file (assuming that directPrint.js is in the same folder as the html file) :
```
<script src="http://code.jquery.com/jquery.min.js" type="text/javascript"></script>
<script src="directPrint.js" type="text/javascript"></script>
```

For example, to print a box of 10 character spaces with a center-aligned string "test" :
```
<div class="dPrint topLeft drawLine[repeat[10]] topRight newLine"></div>
<div class="dPrint vLine"></div>
<div class="dPrint format[center[10]]">test</div>
<div class="dPrint vLine newLine"></div>
<div class="dPrint bottomLeft drawLine[repeat[10]] bottomRight newLine"></div> 
```


and then to print the boxed string :
```
<script> 
directPrint.setPrinterName('LX300'); 
directPrint.init('.dPrint'); //this is simply a jQuery selector 
directPrint.print(); 
</script> 
```


It can be extended to print character(s) that hadn't been included internally. For example for using with Epson POS TM-U220 :
```
directPrint.init('.dPrint' , {
 emphasized        : directPrint.chr(27) + directPrint.chr(69) + 1,
 noEmphasized      : directPrint.chr(27) + directPrint.chr(69) + 0,
 black             : directPrint.chr(27) + directPrint.chr(114) + 0,
 red               : directPrint.chr(27) + directPrint.chr(114) + 1,
 font0             : directPrint.chr(27) + directPrint.chr(33) + directPrint.chr(16),
 cancelStyle       : directPrint.chr(27) + directPrint.chr(33) + directPrint.chr(0),
});
```

It will clip the text if the content is longer than reserved space.


