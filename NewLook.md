![http://lh3.ggpht.com/_9hmP3Ho0t14/TUYf2eqTORI/AAAAAAAAAfQ/HDRByxbz5BY/top.png](http://lh3.ggpht.com/_9hmP3Ho0t14/TUYf2eqTORI/AAAAAAAAAfQ/HDRByxbz5BY/top.png)
[![](http://lh4.ggpht.com/_9hmP3Ho0t14/TUYf2osL_0I/AAAAAAAAAfU/wAMhDzK00kw/bottom.png)](http://code.google.com/p/jzebra/wiki/ScreenShots)

# Features #
  * Prints barcodes, receipts and more from a web page.
  * Supports thermal printers, label printers, magnetic cards.
  * 100% free and [open source](http://www.gnu.org/licenses/gpl.html)
  * Free to use in commercial applications (check [license](http://www.gnu.org/licenses/gpl.html) for details)
  * Seamlessly sends commands to your EPL2, ZPLII, CHR, ASCII, RAW, ESC/P printer (and more).
  * Compatible with Windows, Mac OS X, Ubuntu, Solaris (and more).
  * Tested with Firefox, Safari, Internet Explorer, Opera.
  * Supports COM, parallel, serial, USB, socket, lpr, LPT communication.
  * AJAX compatible by using JavaScript to control print jobs


---



# How It Works #
  1. First, jZebra loads in your web browser as a Java applet (similar to a Flash or SilverLight object).
  1. Second, jZebra interfaces with browser interactively via JavaScript.
  1. Third, jZebra gains permission to use locally installed printers via digital signature prompt.
  1. Finally, jZebra spools directly to locally installed printers, allowing hundreds of print jobs to transfer seamlessly from web code to printer.


---



# Getting Started #
  * Start using jZebra now by [downloading the latest version](http://code.google.com/p/jzebra/downloads/list).
  * Learn jZebra's features step-by-step and how to integrate jZebra into your web project using the [developers guide](TutorialWebApplet.md).
  * Last, read more about purpose and the history of jZebra [here](About.md).

> [![](http://lh6.ggpht.com/_9hmP3Ho0t14/TUY20GlXmMI/AAAAAAAAAfc/7UCka5D18D0/download.png)](http://code.google.com/p/jzebra/downloads/list)

> [![](http://lh5.ggpht.com/_9hmP3Ho0t14/TUY20LN-yDI/AAAAAAAAAfg/BXR9r0sJQfw/tutorial.png)](http://code.google.com/p/jzebra/wiki/TutorialWebApplet)



---



# Configure Your Printer #
  * [Windows](TutorialRawXP.md):
> [![](http://lh4.ggpht.com/_9hmP3Ho0t14/TUY71-4iWjI/AAAAAAAAAfw/5ZUSa8oJucA/windows.png)](http://code.google.com/p/jzebra/wiki/TutorialRawXP#Introduction)
  * [Ubuntu](TutorialRawUbuntu.md):
> [![](http://lh6.ggpht.com/_9hmP3Ho0t14/TUY71nqJWtI/AAAAAAAAAfs/VR957D7QStc/ubuntu.png)](http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu#Introduction)
  * [Mac](TutorialRawOSX.md):
> [![](http://lh6.ggpht.com/_9hmP3Ho0t14/TUY71SLGnnI/AAAAAAAAAfo/Rd9rFtxmKZ8/mac.png)](http://code.google.com/p/jzebra/wiki/TutorialRawOSX#Introduction)


---



# Spotlight #
  * [ups-php](http://code.google.com/p/ups-php/) uses jZebra
  * [RocketShip.it](http://rocketship.it/) uses jZebra
  * [Reason Transport](http://www.reasontransport.com/) uses jZebra
  * [Turning Stone Resort and Casino](http://www.turningstone.com/members/) uses jZebra
  * [FedEx Developer Site](http://justtesting.biz/html/jzebra/jzdemo.html) uses jZebra
  * [Zenkraft.com](http://www.zenkraft.com) uses jZebra
  * [Store4Schools](http://store4schools.com) uses jZebra





---


# Update History #
  * `01/30/2011:` Site redesign
  * `01/12/2011:` Version 1.1.1 available (not featured, see downloads).  Adds a new `appendFile()` feature similar to original 1.0.3 and older functionality `CONFIGPATH="http://site/epl.txt"`.
  * `01/08/2011:` Version 1.1.0 available.  Fixes XML parsing error discovered in Internet Explorer.  Please note, the JavaScript in sample.html has timing improvements added in lieu.
  * `01/07/2011:` Version 1.0.9 available.  Adds experimental [Cp1252](http://en.wikipedia.org/wiki/Windows-1252) support, [XML message parsing](http://code.google.com/p/jzebra/wiki/TutorialWebApplet#XML_Printing) support.
  * `12/08/2010:` Version 1.0.7 available for improved digital signature support.  Versions 1.0.7 and higher will use the same trusted java signature: see source:/jzebra.ks.
  * `11/20/2010:` Version 1.0.6 available for download.  Added feature that allows larger print jobs to be spooled as separate jobs to the printer. (Example, every 5 labels spools a new print job)
  * `01/06/2010:` An excellent article ["RAW Printing from Web Based Application"](http://paparadit.blogspot.com/2010/06/raw-printing-from-web-based-application.html)
  * `04/13/2010:` Version 1.0.5 available for download.  Fixed "Magic Cookie" issue thank to James at ZenKraft.
  * `12/03/2009:` Updated applet tutorial for version 1.0.4.
  * `11/19/2009:` Version 1.0.4 available for download.  Note:  Code changes will need to be made to incorporate new version!!
  * `11/07/2009:` Uploaded more [screenshots](ScreenShots.md) for Ubuntu 9.10 and Windows XP.
  * `11/06/2009:` [Raw Printing from Mac OSX](TutorialRawOSX.md) created in [wiki](http://code.google.com/p/jzebra/w/list) section
  * `10/24/2009:` [ReasonTransport](http://reasontransport.com) to test Bluetooth printing capabilities
  * `01/09/2009:` [TutorialWebApplet](TutorialWebApplet.md) added to [wiki](http://code.google.com/p/jzebra/w/list) for 1.0.3 usage
  * `12/30/2008:` jZebra 1.0.3 pre-release avaiable:  Check the [downloads](http://code.google.com/p/jzebra/downloads/list).
  * `11/07/2008:` jZebra 1.0.3 under development:  Check [SVN](http://code.google.com/p/jzebra/source/checkout) if curious.
  * `11/06/2008:` Added 1.0.2 Bugs/Issues: [click to review issues](http://code.google.com/p/jzebra/issues/list)


---




### Printers Reported Working ###
  * Samsung Bixolon SRP350plus
  * Telly Dascom 1125 (USB)
  * Epson Thermal Printer (COM)
  * Eltron P310i
  * Zebra P310i
  * Zebra LP 2844
  * Zebra TLP2844
  * Citizen CT-S2000 (USB)
  * DOS/LPT1 Printing - Character encoding on some platforms breaks and is being worked on.

Related projects:
http://code.google.com/p/ups-php/
http://code.google.com/p/zxing/
http://www.google.com/chrome/intl/en/p/cloudprint.html

Keywords:
zpl, pcl, prn, txt, ps, eps, direct, ESC k, ESC p, ESC/P, Epson Standard Code for Printers, &H1B, HEX, (1BH), CHR(27), ESC, ASCII, CHR$, BASIC, Cloud Printing, PHP, ASP.NET, print dos characters from web browser