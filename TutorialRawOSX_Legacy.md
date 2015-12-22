See also:  [Zebra CUPS Documentation](http://code.google.com/p/jzebra/downloads/list?q=zebra_cups) [[mirror](http://www.zebra.com/content/dam/zebra/drivers/en/third-party/ZSN108111-v2.pdf)]


# Introduction #

Here are step-by-step instructions for setting up [raw printing](WhatIsRawPrinting.md) through OS X.  These steps proved successful in getting the [jZebra Applet](http://code.google.com/p/jzebra/wiki/TutorialWebApplet) to print to a raw printer queue from a web page loaded on OS X in Firefox.  _Last tested 11/06/2009, OS X 10.5, CUPS 1.3.8._ ([mirror](http://fatbuttlarry.blogspot.com/2009/11/raw-printing-from-os-x-zebra-printer.html))

| **Note:**  If you are attempting to print to a [LaserJet/DeskJet (PostScript)](WhatIsPostScriptPrinting.md) style printer, these steps are not needed. |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------|


This may resolve issues on OS X described as "Print Error: pstopdffilter/pstocupsraster failed with err number -31000" (thanks to Jean Huliciar).

# Steps #
`Mac OS X 10.5` (In newer versions of OSX, you first may have to type **`sudo cupsctl WebInterface=yes`** in a terminal window)

  1. Load Safari or Firefox to http://localhost:631  and click The "Administration" tab, then "Add Printer"<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSGzEMze1I/AAAAAAAAAPI/KWKjSKHxhmY/s1600/Picture+1.png'><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSGzEMze1I/AAAAAAAAAPI/KWKjSKHxhmY/s400/Picture+1.png' /></a><br><br>
<ol><li>Type the name of your printer and click "Continue"<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSGzZf7RdI/AAAAAAAAAPQ/wVsOful7too/s1600/Picture+2.png'><img src='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSGzZf7RdI/AAAAAAAAAPQ/wVsOful7too/s400/Picture+2.png' /></a><br><br>
</li><li>Be patient as the CUPS server responds to the new printer request<br><a href='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvSGzoGMQHI/AAAAAAAAAPY/Ey5aHQaxQAs/s1600/Picture+3.png'><img src='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvSGzoGMQHI/AAAAAAAAAPY/Ey5aHQaxQAs/s400/Picture+3.png' /></a><br><br>
</li><li>For device, leave default "AppSocket/HP JetDirect" and click "Continue"<br><a href='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvSGzuGogNI/AAAAAAAAAPg/gpeH0vf8bq8/s1600/Picture+4.png'><img src='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvSGzuGogNI/AAAAAAAAAPg/gpeH0vf8bq8/s400/Picture+4.png' /></a><br><br>
</li><li>For URI put the address of the network printer in format "<code>socket://address:port</code>".  Port can be left blank if default (9100).  Click "Continue"<br><table><thead><th><b>Note:</b>  "lpinfo -v" from a terminal might help for USB printers||<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSHxI3sa4I/AAAAAAAAAPw/dSVeNpyzyZQ/s1600/Picture+5.png'><img src='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSHxI3sa4I/AAAAAAAAAPw/dSVeNpyzyZQ/s400/Picture+5.png' /></a><br><br></th></thead><tbody>
</li><li>For Make/Manufacturer, select "Raw" from the list of manufacturers and click "Continue"<br><a href='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvSHxCVBL9I/AAAAAAAAAP4/riLF3pI4yPE/s1600/Picture+6.png'><img src='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvSHxCVBL9I/AAAAAAAAAP4/riLF3pI4yPE/s400/Picture+6.png' /></a><br><br>
</li><li>For "Model" click "Raw Queue (en)" which should be the only option in the drop-down menu.  Click "Add Printer".  Note:  If prompted for a password, enter a username and password with administrative access on the Mac.  You may be prompted twice.<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSHxWL2PII/AAAAAAAAAQA/rnGp4pPml0I/s1600/Picture+7.png'><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSHxWL2PII/AAAAAAAAAQA/rnGp4pPml0I/s400/Picture+7.png' /></a><br><br>
</li><li>Your printer has been added.  You will see a message confirming this. Ignore Banners and Policies prompt.  In the next steps, you will add a Printer Class for your new printer to show in OS X's Print Manager.<br><a href='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvSHxYvp13I/AAAAAAAAAQI/hqX2jl1fPGM/s1600/Picture+8.png'><img src='http://1.bp.blogspot.com/_9hmP3Ho0t14/SvSHxYvp13I/AAAAAAAAAQI/hqX2jl1fPGM/s400/Picture+8.png' /></a><br><br>
</li><li>Click the "Administration" tab and click the "Add Class" button.<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSHxkGyRnI/AAAAAAAAAQQ/r8CWfwM5D7Q/s1600/Picture+9.png'><img src='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSHxkGyRnI/AAAAAAAAAQQ/r8CWfwM5D7Q/s400/Picture+9.png' /></a><br><br>
</li><li>Fill out "Name".  This must not conflict with the printer name from Step 2.   Fill out the "Description" with what you would like the printer listed as in OS X.<br><a href='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSH4gF66tI/AAAAAAAAAQY/fpqCNeHwQcI/s1600/Picture+10.png'><img src='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvSH4gF66tI/AAAAAAAAAQY/fpqCNeHwQcI/s400/Picture+10.png' /></a><br><br>
</li><li>Your printer class has been added.  You will see a message confirming this.<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSH47_spyI/AAAAAAAAAQg/B-14b7kdQMw/s1600/Picture+11.png'><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSH47_spyI/AAAAAAAAAQg/B-14b7kdQMw/s400/Picture+11.png' /></a><br><br>
</li><li>Navigate to "System Preferences" --> "Print and Fax", and your new raw printer should appear.<br><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSH5DpbDlI/AAAAAAAAAQo/hd9-X_3gIv0/s1600/Picture+12.png'><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvSH5DpbDlI/AAAAAAAAAQo/hd9-X_3gIv0/s400/Picture+12.png' /></a><br><br>
</li><li>Your applications should now be able to print to the Zebra printer as a raw printing device.<br>
</li><li>End of Steps</li></ol></tbody></table>

-Tres