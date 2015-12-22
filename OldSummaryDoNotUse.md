# Do not use this tutorial.  It is kept for wiki authoring purposes. Please follow the latest wiki tutorial instead
## Do not use this tutorial, see wiki for latest ##

### API Usage: (for Java developers) ###
To integrate jZebra into your application, simply add `jzebra.jar` to your class path and do the following:
```
import jzebra.PrintRaw;
import javax.print.PrintService;
import javax.print.PrintException;
     // NEEDS RE-WRITE, SORRY     
```

You only have to use the embedded "`lib`" folder when you are utilizing the graphical components of jZebra, such as JApplet, or using it as a stand-alone application.

~~**Note:**  Since `JZebra.class` performs all printing functions, you may us it by itself, or edit `JZebra.java` (in the `src/jzebra` folder) to your liking.  It has been written with NetBeans 6.1 and has an `ant` script included.~~


---


### Applet Usage For Beginners (web developers) ###
**The documentation needs to be more clear.  jZebra needs your help writing it!**

For non-Applet savvy developers, it's recommended to first get the application working on your desktop, as that's where the applet runs from.  Hopefully once understanding it as a desktop application will help getting it to work through an applet.  Here's the steps to get it working on your desktop:
  1. First, ensure Java 5.0 SE or higher is installed on your workstation.
  1. Second, download and extract the program to your desktop so that you have "JZebra.jar" and a "lib" folder.
  1. If you are not running windows, use your Operating System's instructions for getting java.  Fedora users would be using "yum", Ubuntu users would be using "apt-get". A google search will show you more.
  1. Open a console window and launch the program by typing "java -jar /path/to/JZebra.jar".  If you get "java command not found", make sure to add java to your class path.  Note, this is not needed for the applet to work, but will help you with getting your config file.
  1. Paste your raw printer commands into the application.
  1. Check to make sure your printer is selected.  The applet will try to auto-select anything with "zebra" or "eltron" in the name.  This can be specified separately if needed.
  1. If the application prints what you need, next is getting your results into a configurable applet.  Save your raw data into a config file "your\_printer.cfg", and see the advanced usage below.
**Note, all command line parameters can be specified to the applet.**

**Troubleshooting:
  1. Are you using the Zebra driver or a Generic/Text driver?  Generic/Text seems to work better.
  1. Can you send just the test card command to your printer? (Should be available in the documentation for your printer)**


---


### Changes ###

1.0.2:
  * Fixes a web browser applet bug with the XP L&F
  * Fixes printing in "eltron\_p310.cfg" mode with lowercase characters
  * Changed button label from "Print" to "Print Card" in applet mode

### Background ###
Many card printers (such as Zebra or Eltron manufactured printers) need special RAW printer commands sent to them in order to perform certain functions (such as magnetic strip encoding or barcode printing).  These RAW commands are usually sent as text in a proprietary syntax.  This RAW syntax is specified by the printer manufacturer (usually in the form of a developer's manual).  Syntax will vary drastically between printer manufacturers and printer models.

**Note:** RAW commands do not normally need the printer driver, and can be sent using the **Generic/Text driver** supplied with your operating system.

A confusing trait is that even when specifying "RAW" mode in the properties of your print driver, your workstation won't necessarily send RAW printer commands to your card printer.  In my first test case, a Windows workstation and notepad DID NOT produce a usable card.  jZebra is written to work around this.


---


### Summary ###
jZebra was written to give programmers a quick way to send a printer RAW commands that normally WOULD NOT be available with a standard “Windows Printer Driver” and notepad.  This is because modern OSs (as well as modern Java) handle printing from a higher level that does not normally allow low-level RAW commands.

jZebra is a cross platform, cross browser and can even operate GUI-less (batch mode).

**If you find this program useful, please contact a project author with a sample printer file or feedback.**

The Eltron P310 printer, for example, has a [100+ page programmers guide](http://www.youcard.de/service/zebra_prog_guide/Programmers_Guide_980415-001_Rev_B.pdf) for its RAW commands.  Your printer will have its own guide with its own set of RAW commands.

**Note:** This has not been tested, but may work with printers such as Intermec, Tattoo, Pebble, Dualys, Quantum, Securion.  Please use at your own risk.

![http://img177.imageshack.us/img177/7035/cardprintersxt8.png](http://img177.imageshack.us/img177/7035/cardprintersxt8.png)


---


### Prerequisites: ###
  * Java 5 or higher (JRE SE 5.0)
  * Eltron, Zebra, or a printer that talks in RAW mode
  * Appropriate Printer Driver installed on Workstation


---


### General Usage: ###
  1. Download and extract [JZebra.zip](http://code.google.com/p/jzebra/downloads/list) from the downloads section.
  1. Open the `"dist"` folder and double-click `“JZebra.jar”`
  1. Select the Printer that accepts RAW commands (It may auto-select your Eltron or Zebra)
  1. Change commands as necessary.  Text between `/*` and `*/` will be ignored (it is stripped out prior to sending to printer).
  1. You should see the lights on your printer flash quickly, (or equivalent) and a card should print.

**Note:**  If bad commands were sent to the printer, they may be retained in the printer’s memory. Power cycle between testing.

**Note:**  Although jZebra sends RAW commands, it does not read RAW messages.  Troubleshooting in this version is “manual”.


---


### Command Line Usage: (server implimentation) ###
  * jZebra can be launched from a command line with the following syntax:
```
     java –jar /path/to/JZebra.jar “arg1” “arg2” “arg3”
```

> For example (Eltron P310 Specific):

```
     java –jar H:/Applications/JZebra/1.0.0/JZebra.jar “printer=eltron” “firstname=John” “lastname=Doe” “accountno=1234” “companyno=4321”
```

For a complete list of command line options, use the argument “--help”.

**Note:**  Please surround all commands with double-quotes.


---


### Web Usage: (advanced web developers) ###
  * jZebra is enabled for both Webstart (Launch from web page) and Applet (Launch inside a web page).
  * **Webstart:**  Simply provide a link on your page to the included `launch.jnlp`, and ensure the `JZebra.jar` and `lib` folder reside on the web server.   You may decide to use a graphic as follows (recommended).
![http://img519.imageshack.us/img519/9117/samplejnlpfi9.png](http://img519.imageshack.us/img519/9117/samplejnlpfi9.png)

**Note:** jZebra does not (yet) allow parameters through the `launch.jnlp` URL.  This is possible, but has not yet been implimented.

  * **Applet:**  An applet is possible through the use of HTML object code.  jZebra is enabled for applet mode, but will look considerable different than when running through other modes.  Here is the code needed to embed jZebra into your web page:

```
     // DEPRECATED.  NEEDS REWRITE
```
![http://img507.imageshack.us/img507/8107/testappletfc4.png](http://img507.imageshack.us/img507/8107/testappletfc4.png)

This Print button can be placed in any portion of your web page.

You will notice that these fields will need to be generated dynamically, most commonly through the use of server-side ASP or PHP.  If you create a JavaScript implementation, please forward it to the developer(s).


---



### Advanced Usage: ###
jZebra has some advanced features:
  * Headless: More commonly known as “batch” mode where no GUI will be used, simply pass in the parameter “`headless`”.

**Note:**  This mode has not been extensively tested.

  * Config Override:  For other printer types, you may specify a local or remote configuration file.  Think of this as an "answer file" with all of your RAW commands in it.  To do this, pass in the parameter:

```
     “config=protocol:/path/to/config”
```

where protocol can be `http`, `ftp`, `file`, or a resource (in `/jzebra/resources`).

**Note:** Currently Only the `eltron_p310.cfg` is included in resources.

**~~Line Number Override:  Each command in a config can be individually overridden by specifying the line number and the entire command to override it with (Carriage Returns are automatically included).  To do this, pass in the parameter:~~**

```
     // DEPRECATED
```

  * If you are using ZPL or an old Eltron configuratino, you'll notice Zebra printers don't like the initial reset command.  To strip this out of the `eltron_p310.cfg`, pass in the following parameter:

```
     // DEPRECATED
```


---


### API Usage: ###
See above.

Enjoy!