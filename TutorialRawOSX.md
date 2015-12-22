For raw printers only.  If unsure please see [WhatIsRawPrinting](WhatIsRawPrinting.md)

# Background #

These steps will allow a USB or Network attached printer to receive raw commands through a Safari web browser on OSX.  This will also work for any 64-bit capable browser, such as Firefox that can run Java applets.  At the time of writing this, Chrome for OSX is 32-bit only and will not work with Oracle Java 1.7 64-bit runtime.

The sample.html provided with jZebra is intended to run from the local file system, however Safari will not run the applet unless it is hosted from a web server.  [MAMP](http://www.mamp.info) is recommended for this, which will run a portable web server on your Mac Desktop.  Installing and configuring MAMP is outside the scope of this tutorial.  Alternately, you can use Firefox and MAMP will not be needed.

# Adding a Raw Printer #
  1. Visit **http://java.com/verify/** to confirm Java is installed and running properly
    * Optional:  Enable the Java console in System Preferences, Java, Advanced, Java Console, Show Console (Highly recommended for web developers)
  1. Open a Terminal window: **⌘+space, `terminal`, enter**
  1. Enable CUPS web interface by entering this into the Terminal <br><b><code>sudo cupsctl WebInterface=yes</code></b>
<ol><li>Load Safari to the CUPS web interface <b><a href='http://localhost:631'>http://localhost:631</a></b>  and click The "Administration" tab, then "Add Printer"<br><img src='http://i.imgur.com/Dl0yvlM.png' />
</li><li>If you see your USB raw printer in the listing <b>DO NOT</b> select it.<br>
</li><li>Click <b>AppSocket/HP JetDirect</b>, Continue. [<a href='http://i.imgur.com/IETpAWh.png'>screenshot</a>]<br>
</li><li>You will be prompted for a port<br>
<ul><li>For USB printers type: (Example)<br><b><code>usb://Zebra/LP2844</code></b><br><i>Get this port by issuing the command <b><code>lpinfo -v |grep usb:</code></b> from the Terminal.  You don't need the "?location=1a200000" information. [<a href='http://i.imgur.com/s3mWBVh.png'>screenshot</a>]</i>
</li><li>For network printers type: (Example)<br><b><code>socket://192.168.254.254:9100</code></b><br>The IP address may be configured to use a different address, which is outside of the scope of this tutorial.<br>
</li></ul></li><li>Enter an appropriate Name, Description and Location for your printer<br><img src='http://i.imgur.com/FgyBYZ0.png' />
</li><li><b>Do not share printer</b>, Continue.<br>
</li><li>Make: <b>Raw</b>, Continue [<a href='http://i.imgur.com/9SVP96k.png'>screenshot</a>]<br>
</li><li>A summary will display.  Click <b>Add Printer</b>
</li><li>Starting Banner: <b>none</b>, Ending Banner: <b>none</b>.  Click <b>Set Default Options</b>
</li><li>You may now print to your printer.  Continue to the next section <b>Adding a Printer Class</b> to make the printer appear in System Preferences, Print & Scan</li></ol>

<h1>Adding a Printer Class</h1>
<ol><li>From the CUPS web interface, click <b>Administration</b>, <b>Add Class</b> [<a href='http://i.imgur.com/vu40UK7.png'>screenshot</a>]<br>
</li><li>Enter an appropriate Name, Description and Location for your class.  It must differ from the raw printer name chosen previously.<br>
</li><li>In <b>Members</b>, Select the <b>raw printer name</b> chosen previously, <b>Add Class</b>
</li><li>In <b>System Preferences</b>, <b>Print & Scan</b>, your new printer class will be listed.  You may use this to monitor print jobs. [<a href='http://i.imgur.com/yHCHZwZ.png'>screenshot</a>]</li></ol>

Continue to <a href='TutorialWebApplet.md'>TutorialWebApplet</a> for printing a test page from Safari<br>
<br>
-Tres