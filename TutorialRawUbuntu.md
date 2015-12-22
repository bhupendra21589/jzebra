# Updated tutorial here: http://qzindustries.com/TutorialRawUbuntu #

See also:  [Zebra CUPS Documentation](http://code.google.com/p/jzebra/downloads/detail?name=zebra_cups.pdf) (mirror)

See also:  [Epson Ubuntu Blog Article](http://code.google.com/p/jzebra/downloads/detail?name=epson_stylus_ubuntu.pdf)  (mirror)

# Introduction #

| **Note:**  Ubuntu has significantly changed the interface for the Unity desktop making this tutorial out-dated.  Please help improve this wiki by becoming a contributor.  Email tres.finocchiaro@gmail.com for contributor access. |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Here are step-by-step instructions for setting up [raw printing](WhatIsRawPrinting.md) on Ubuntu. These steps proved successful in getting the jZebra Applet to print to a raw printer queue from a web page loaded on Ubuntu 9.10 in Firefox. _Last tested 11/06/2009, Ubuntu 9.10, CUPS 1.3.8._ [(mirror)](http://fatbuttlarry.blogspot.com/2009/11/raw-printing-from-ubuntu-910-zebra.html)

| **Note:**  If you are attempting to print to a [LaserJet/DeskJet (PostScript)](WhatIsPostScriptPrinting.md) style printer, these steps are not needed. |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------|


# Steps #
`Ubuntu 9.10`


  1. From the desktop, click "**System --> Administration --> Printing**" <br><img src='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvU05p2LY3I/AAAAAAAAARw/dOBH7_Bi44U/s400/1.png' /><br><br>
<ol><li>Click "<b>New</b>" (Printer) <br><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvU05szIyqI/AAAAAAAAARo/E6JRqbDVhcY/s400/2.png' /><br><br>
</li><li>Be patient while Ubuntu searches for printers... <br><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvU05QgtgyI/AAAAAAAAARg/oQkNRrSYPb0/s400/3.png' /><br><br>
</li><li>Select "<b>Network Printer --> AppSocket/HP JetDirect</b>". For host, put the IP address or hostname of your printer.  Port is usually default of 9100. Click "<b>Forward</b>" <br>
<blockquote><table><thead><th> <b>Note:</b> If the printer is locally attached to the client system, we should not be selecting a network printer, instead the correct port. </th></thead><tbody>
<img src='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvU0xh3mRaI/AAAAAAAAARY/IOkWdck2OCo/s400/4.png' /><br><br>
</blockquote></li><li>Select printer make "<b>Generic</b>".  Click "<b>Forward</b>". <br><img src='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvU0xbQgGFI/AAAAAAAAARQ/TkK8DZTewg0/s400/5.png' /><br><br>
</li><li>Click model "<b>Raw</b>", Drivers "<b>Generic Raw Queue <a href='en.md'>en</a></b>".  Click "<b>Forward</b>". <br><img src='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvU0xVFE02I/AAAAAAAAARI/LwQp4LaGsLk/s400/6.png' /><br><br>
</li><li>Name the printer appropriately such as "<b>zebra</b>".  Click "<b>Apply</b>". <br><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvU0xNaWrqI/AAAAAAAAARA/bFV_ln9vjrg/s400/7.png' /><br><br>
</li><li>Your new printer "zebra" should now list.  You can now use this as a raw print queue. <br><img src='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvU0w2PZVrI/AAAAAAAAAQ4/5541dsaKfMI/s400/8.png' /><br><br>
</li><li>End of Steps</li></ol></tbody></table>

-Tres