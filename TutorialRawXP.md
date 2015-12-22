# Introduction #
Here are step-by-step instructions for setting up [raw printing](WhatIsRawPrinting.md) on Windows XP. These steps proved successful in getting the jZebra Applet to print to a raw printer queue from a web page loaded on Windows XP in Firefox and Internet Explorer. _Last tested 11/07/2009, Windows XP SP2_ ([mirror](http://fatbuttlarry.blogspot.com/2009/11/raw-printing-from-windows-xp-zebra.html))

| **Note:**  If you are attempting to print to a [LaserJet/DeskJet (PostScript)](WhatIsPostScriptPrinting.md) style printer, these steps are not needed. |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------|

# Scripting #
  * Advanced use only!  Read Steps below before attempting to script this process!
  * Rather script this?  From a command prompt window try this:

```
      rundll32 printui.dll,PrintUIEntry /if /b "Zebra" /f "%WINDIR%\inf\ntprint.inf" /r "lpt1:" /m "Generic / Text Only"
```

  * Replace "lpt1:" with your port, such as "COM5:", etc.  USB ports generally need drivers installed first for port to show up.
  * Advanced options, look here: http://www.robvanderwoude.com/2kprintcontrol.php
  * If you need to script a network port, please look here:  http://users.telenet.be/mydotcom/howto/scripts/sysadmin/printers_tcpip.htm

# Steps #
`Windows XP`

(Note, on Windows 8 use "Advanced Printer Setup")

  1. Open Control Panel. Click "**Printers and Faxes**"<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvW2L2lQwJI/AAAAAAAAATw/THPg257TKgo/s1600-h/1.png'><img src='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvW2L2lQwJI/AAAAAAAAATw/THPg257TKgo/s400/1.png' /></a><br><br>
<ol><li>Click "<b>Add Printer</b>"<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW2HPoatcI/AAAAAAAAATo/IqHiAh4bj6g/s1600-h/2.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW2HPoatcI/AAAAAAAAATo/IqHiAh4bj6g/s400/2.PNG</a><br><br>
</li><li>Click "<b>Next</b>" at the welcome screen.<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW2HL22vxI/AAAAAAAAATg/gc9Oc-1MOiE/s1600-h/3.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW2HL22vxI/AAAAAAAAATg/gc9Oc-1MOiE/s400/3.PNG</a><br><br>
</li><li>Click "<b>Local printer attached to this computer</b>" and deselect "<del><b>Automatically detect and install...</b></del>". Click "<b>Next</b>".<br><a href='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW2G2hBa0I/AAAAAAAAATY/VPSh7MXHW0s/s1600-h/4.PNG'>http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW2G2hBa0I/AAAAAAAAATY/VPSh7MXHW0s/s400/4.PNG</a><br><br>
</li><li>Click "<b>Create New Port</b>" and from the drop-down select "<b>Standard TCP/IP</b>" port.<br><a href='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW2Gnum5xI/AAAAAAAAATQ/wdCkE1JUmW0/s1600-h/5.PNG'>http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW2Gnum5xI/AAAAAAAAATQ/wdCkE1JUmW0/s400/5.PNG</a><br><br>
<ul><li>For <b>COM Ports</b>, instead of creating a new TCP/IP port, use an existing port and chose your COM port (COM1, COM2, etc)<br>
</li><li>For <b>Parallel Ports</b>, instead of creating a new TCP/IP port, use an existing LPT port (LPT1, LPT2, etc).<br>
</li><li>For <b>USB Ports</b>, instead of creating a new TCP/IP port, use the available USB port.  This is tricky as the USB port doesn't always list as an available port.  In the past I've had to install the printer drivers first to list the USB port, and then change the driver to Generic/Text afterward.<br>
</li></ul></li><li>At the Port Wizard Welcome screen click "<b>Next</b>"<br><a href='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW2GoWylHI/AAAAAAAAATI/h2imLtUSAZk/s1600-h/6.PNG'>http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW2GoWylHI/AAAAAAAAATI/h2imLtUSAZk/s400/6.PNG</a><br><br>
</li><li>For Printer Name or IP Address, put the hostname or IP of your printer and click "<b>Next</b>"<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW10LcSyUI/AAAAAAAAATA/kd0tcqX_FLk/s1600-h/7.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW10LcSyUI/AAAAAAAAATA/kd0tcqX_FLk/s400/7.PNG</a><br><br>
</li><li>If prompted for a Device Type, select "<b>Generic Network Card</b>". Click "<b>Next</b>".<br><a href='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW1z9kZCPI/AAAAAAAAAS4/UkRxy6kW3P4/s1600-h/8.PNG'>http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW1z9kZCPI/AAAAAAAAAS4/UkRxy6kW3P4/s400/8.PNG</a><br><br>
</li><li>A summary page will display with your port information. Click "<b>Finish</b>".<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1zjA4nBI/AAAAAAAAASw/UTbFFGFmTMM/s1600-h/9.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1zjA4nBI/AAAAAAAAASw/UTbFFGFmTMM/s400/9.PNG</a><br><br>
</li><li>The Printer Wizard will continue. When prompted for Manufacturer, click "<b>Generic</b>". For printer, select "<b>Generic/Text Only</b>". Click "<b>Next</b>".<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvW1zc6-UnI/AAAAAAAAASo/cosdqEsoc2k/s1600-h/10.PNG'>http://3.bp.blogspot.com/_9hmP3Ho0t14/SvW1zc6-UnI/AAAAAAAAASo/cosdqEsoc2k/s400/10.PNG</a><br><br>
</li><li>If prompted to keep the driver, click "<b>Keep the existing driver</b>". Click "<b>Next</b>".<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1zQlZvqI/AAAAAAAAASg/EbADuqx8uz0/s1600-h/11.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1zQlZvqI/AAAAAAAAASg/EbADuqx8uz0/s400/11.PNG</a><br><br>
</li><li>Type the printer name you'd like to use. For example, "<b>zebra</b>". It will ask to use this printer as the default printer. Click "<b>No</b>". Click "<b>Next</b>".<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1onvAmWI/AAAAAAAAASY/JChPSKKJPT0/s1600-h/12.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1onvAmWI/AAAAAAAAASY/JChPSKKJPT0/s400/12.PNG</a><br><br>
</li><li>When prompted to share the printer, click "<b>Do not share this printer</b>". This setting can be changed later if needed.<br><a href='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW1ocbvBQI/AAAAAAAAASQ/bSneNnnfGyU/s1600-h/13.PNG'>http://4.bp.blogspot.com/_9hmP3Ho0t14/SvW1ocbvBQI/AAAAAAAAASQ/bSneNnnfGyU/s400/13.PNG</a><br><br>
</li><li>You will be prompted to print a test page. Click "<b>No</b>" and click "<b>Next</b>".<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1oIOGa1I/AAAAAAAAASI/G_PK0LFY984/s1600-h/14.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1oIOGa1I/AAAAAAAAASI/G_PK0LFY984/s400/14.PNG</a><br><br>
</li><li>The wizard summary page will appear. Click "<b>Finish</b>"<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1n-efNzI/AAAAAAAAASA/8zB0EO0Eeto/s1600-h/15.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SvW1n-efNzI/AAAAAAAAASA/8zB0EO0Eeto/s400/15.PNG</a><br><br>
</li><li>Your printer will now list under "<b>Printers and Faxes</b>"<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvW1n0SgOhI/AAAAAAAAAR4/GRj8UtzVSmA/s1600-h/16.PNG'>http://3.bp.blogspot.com/_9hmP3Ho0t14/SvW1n0SgOhI/AAAAAAAAAR4/GRj8UtzVSmA/s400/16.PNG</a><br><br>
</li><li>Troubleshooting: (If problems exist) Make sure the new port (under the new printer <b>properties --> ports --> find your new port --> configure port</b>) is set to "<b>RAW</b>" under protocol. If printing to a non-standard port (other than 9100) adjust the port settings correctly.<br><br>
</li><li>End of Steps</li></ol>

-Tres