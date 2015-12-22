[![](https://www.paypalobjects.com/WEBSCR-640-20110306-1/en_US/i/btn/btn_donate_LG.gif)](http://code.google.com/p/jzebra/wiki/Donations)

# Support #
jZebra is offered as is without any warranty.  Email support is provided as a courtesy with no guarantees.  In the event contracted/paid support is needed, contact the [author](mailto:tres.finocchiaro@gmail.com) for arrangements.

# Introduction #
If you are looking to send raw (industry/production) printer commands to your printer with php, jsp, ASP or JavaScript you likely have found -- until now -- the only option is a proprietary Microsoft-only ActiveX control for Internet Explorer.  jZebra is an open-source and open-API alternative.

jZebra will not work with mobile devices such as smart phones.  This is a limitation of 1. Lack of JRE 1.5 Java support and 2. Lack of Java Applet support on mobile web browsers. If this changes in the Android or iOS/iPhone/iPad market, the site will be updated to reflect that.

If the printer is NOT a Zebra printer, jZebra **may still work** for your printer and application!


# Supported Printers #
  * Any printer capable of accepting raw print commands should work with jZebra.  This includes USB, Parallel, Serial (COM Port), Virtual COM Port (Virtual COM Servers), Network Printers.
  * For a quick reference, contact your printer manufacturer to find out if the printer is capable of EPL (1 or 2), ZPL (I & II), ESC/P.  These are the most common and will get the quickest help via jzebra-users@googlegroups.com mailing list.
  * Note, other raw print languages are supported as well, but success will depend on experience with Hex, Unicode, JavaScript and Character Encoding.  Project help is greatly needed on these fronts.
  * PostScript support is limited but working which allows jZebra to print to LaserJet, InkJet style printers.  Search "printPS()" on the wiki for usage.

# Versions #
jZebra 1.4.x slated for December 2012 is planned to add scale support through serial connectivity.  jZebra 2.0.0 will be a rewrite to the entire 1.4.x codebase to reduce size, increase stability and eliminate threading and race conditions.
jZebra 1.0.5 (44KB) and higher is lighter-weight rewrite of version 1.0.3. Newer versions are based on 1.0.5 and geared specifically for JavaScript usage with enhancements for special characters/special print commands.  It is recommended you start with the [latest featured version](http://code.google.com/p/jzebra/downloads/list?q=label:Featured) from downloads section.   jZebra can work with multiple web browsers including Internet Explorer, Opera, Safari, Firefox, Chrome.

jZebra 1.0.3 (202KB) Is listed in the download under "obsolete", but features an in-browser applet, a desktop application, and command line batch support.  These features were removed in newer versions to reduce the download size.

Future jZebra versions will be tailored according to industry needs and focus new developments on COM port and BlueTooth support.


# Details #
jZebra sends raw information to your printer by bypassing the standard PCL (printer control language) and sending raw data directly to your printer.  In the production industry, this raw printing functionality is often required for making badges, tags (RFID, magnetic strip), receipts (thermal paper) and labels (bar-codes, asset tags) from Zebra printers.  jZebra has been tested with non-zebra printers too!


# API/License #
jZebra is a completely free, open-source Java application using open Java APIs.  As of 5/7/2013, all versions of jZebra are licensed LGPL 2.1 which allows it to be used without modification for virtually all purposes.  This means jZebra can be used with open source, closed source and even be sold with a product.  However, if you re-use or modify the source code of jZebra, you are legally obligated to publish your changes in accordance with the LGPL 2.1 license.  If you wish to make a copy of the source code and re-release it under a GPL2+ or GPL3+, you are free to do so, however all other license changes must be approved in writing by Tres Finocchiaro.

jZebra can be included in your Java projects directly through it's [API](TutorialAPI.md), or loaded as a [web applet](TutorialWebApplet.md).

| **Note:** In return for offering this free plugin, jZebra would like written permission to list your company on the [front page](http://code.google.com/p/jzebra/#Spotlight), although this is not mandatory. :) |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

For use in your **web page**, see the [Web Applet Wiki](http://code.google.com/p/jzebra/wiki/TutorialWebApplet)

Please help contribute to the jZebra wiki if you find this product useful by becoming a project contributor, or email the [author](mailto:tres.finocchiaro@gmail.com) with comments, feedback, code examples, suggestions, etc.  All forms of feedback are welcome.

# History #
jZebra was initially created for [magnetic stripe encoding](http://en.wikipedia.org/wiki/Magnetic_stripe_card), such as hotel room keys or player tracking cards on Zebra™ style printers.  Zebra™ printing is the most common use of jZebra due to the growing demand for a web page that can perform thermal/bar-code or magnetic-stripe printing.

Since its creation, jZebra has shown more interest in its capabilities in printing bar-codes for shipping purposes.  Not to be confused with the [Barbecue](http://barbecue.sourceforge.net)  project... The jZebra project is working with the [ups-php](http://code.google.com/p/ups-php/) project, a web developer from [ReasonTransport](http://www.reasontransport.com/) and also a web developer from [FedEx](http://www.justtesting.biz/html/jzebra/jzdemo.html) to focus its usage web use for packaging and shipping automation by printing thermal-printer labels and bar-codes.  If you have questions on whether or not jZebra will work for you, please contact [the author](mailto:tres.finocchiaro@gmail.com).

-Tres