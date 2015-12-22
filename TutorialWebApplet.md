**Tip:** Hit <CTRL + F> and search this page for keywords!!

# Introduction #
This is a tutorial for web developers to add a web applet to your page capable of sending raw commands to your printer.  This is common for Barcodes, Thermal Printing, Point-Of-Sales (POS), and other commercial/industry purposes.

This is possible by using JavaScript to talk to Java through the "Applet" interface that is provided by all major web browsers.

Download and extract a [featured version](http://code.google.com/p/jzebra/downloads/list?can=3).  There's a bunch of files, but we'll primarily be using **"sample.html"**.  Also make sure **"qz-print.jar"** resides in the same folder/location.

https://jzebra.googlecode.com/files/unzip-screenshot.PNG


The sample runs client-side.  No uploading to a web server is needed for this tutorial.

There are separate buttons for each type of printing, so study them closely.  Behind each button is a small snippet of JavaScript code for interacting with the qz-print applet.

https://jzebra.googlecode.com/files/sample-html.PNG

> | **Note:** qz-print requires Java 5 or higher to run.  For help installing Java on your platform, see the [Java tutorial](TutorialJavaInstall.md). |
|:--------------------------------------------------------------------------------------------------------------------------------------------------|

The steps below walk through adding an applet to your web page, and explain how to interact with it through JavaScript.


---

# Steps #
## Load The Applet ##
  1. Make sure your printer is set up on your workstation with the name "zebra" (this can be changed later).
  1. Make sure printer is connected as a raw print queue for your operating sytem (Click the Windows, Ubuntu, or Mac logo for details)
> > [![](http://3.bp.blogspot.com/_9hmP3Ho0t14/SvXbFLIbfXI/AAAAAAAAAUQ/EmPDrWLk7YI/s400/config_win.png)](http://code.google.com/p/jzebra/wiki/TutorialRawXP#Steps)[![](http://4.bp.blogspot.com/_9hmP3Ho0t14/SvXbE4Sp39I/AAAAAAAAAUI/dvvUZ_sJNQA/s400/config_lin.png)](http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu#Steps)[![](http://2.bp.blogspot.com/_9hmP3Ho0t14/SvXbE_kTK_I/AAAAAAAAAUA/a-Ucl9UaIvI/s400/config_mac.png)](http://code.google.com/p/jzebra/wiki/TutorialRawOSX#Steps)![http://2.bp.blogspot.com/_9hmP3Ho0t14/SvXbEnoMELI/AAAAAAAAAT4/eF4xkJ68ALY/s400/config_end.png](http://2.bp.blogspot.com/_9hmP3Ho0t14/SvXbEnoMELI/AAAAAAAAAT4/eF4xkJ68ALY/s400/config_end.png)
  1. Download the [latest version](http://code.google.com/p/jzebra/downloads/list) and extract the contents to your desktop.  Open "sample.html" with a web browser.
    * The following applet code creates the applet.
```
    <html><body>
       <applet id="qz" name="QZ Print Plugin" code="qz.PrintApplet.class" archive="./qz-print.jar" width="100" height="100"></applet><br><br>
    </html></body>
```
    * The html file should reside in the same folder as `qz-print.jar`.  Alternately, you can move the JAR to a different location so long as you change `archive="./qz-print.jar"` to match your new location.
> > | **Note:** Java 7 + Apache users:  Change apache config to use "SSLStrictSNIVHostCheck on" and restart apache.  read more here https://bitbucket.org/StrangeWill/redmine-inline-attach-screenshot/issue/17/java-17-unrecognized_name-due-sni-support |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> > | **Note:** Chrome users may receive a message "The Java plug-in requires your permission to run". Click "Always run on this site"<br><br> <img src='http://jzebra.googlecode.com/files/permission.jpg' />                                            <br>
<blockquote><tr><td> <b>Note:</b> IE7 may receive an ActiveX warning. Click "Allow Blocked Content"<br><br> <img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SxgmMqgJQAI/AAAAAAAAAW4/WBkVhYcg4no/s400/blocked_content.png' />                                             </td></tr>
<tr><td> <b>Note:</b> IE7 may be prompt to Click to Activate This Control each time the applet loads.  Click <a href='http://www.mix-fx.com/flash-prompt.htm'>here</a> for details.                                                                          </td></tr>
</blockquote><ol><li>The applet will begin to load in the web page.<br>
<blockquote><tr><td> <b>Note:</b> Chrome users on Linux with outdated plugins, launch chrome with "<code>google-chrome --always-authorize-plugins --allow-outdated-plugins</code>".  This will allow Java to load in Chrome without warnings of outdated plugins!        </td></tr>
<blockquote><a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SxgoGt3lmKI/AAAAAAAAAXA/jsqVvrlRl4k/s400/applet_loading.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SxgoGt3lmKI/AAAAAAAAAXA/jsqVvrlRl4k/s400/applet_loading.PNG</a>
</blockquote></blockquote></li><li>Next, Java security dialog prompt is shown.  Click "Run".<br>
<blockquote><a href='https://jzebra.googlecode.com/files/trusted-warning.PNG'>https://jzebra.googlecode.com/files/trusted-warning.PNG</a>
</blockquote></li><li>The applet should be loaded.  At this point it will look like a plain html page with a few sample buttons.<br>
<blockquote><a href='https://jzebra.googlecode.com/files/sample-html.PNG'>https://jzebra.googlecode.com/files/sample-html.PNG</a>
</blockquote></li><li>Right click the Java system tray icon (Windows) and clicking "<a href='http://img74.imageshack.us/img74/2423/jzebrajava1tx5.png'>Open Java Console</a>".  Linux Oracle Java users run: <code>jcontrol</code> --> Advanced --> Java Console --> Show Console.  Linux OpenJDK users, run the web browser from a command line.<br>
<blockquote><tr><td> <b>Note:</b> The Java Console is critical for calibrating qz-print for your printer.                                                                                                                                                                </td></tr>
</blockquote></li><li>You should see the version of qz-print <code>"INFO: qz-print 1.x.x"</code> followed by <code>"===== JAVASCRIPT LISTENER THREAD STARTED ====="</code> in the log.  Sample:<b><br>
<pre><code>       Java Plug-in 10.45.2.18<br>
       Using JRE version 1.7.0_45-b18 Java HotSpot(TM) Client VM<br>
       User home directory = %USERPROFILE%<br>
       ----------------------------------------------------<br>
       c:   clear console window<br>
       f:   finalize objects on finalization queue<br>
       g:   garbage collect<br>
       h:   display this help message<br>
       l:   dump classloader list<br>
       m:   print memory usage<br>
       o:   trigger logging<br>
       q:   hide console<br>
       r:   reload policy configuration<br>
       s:   dump system and deployment properties<br>
       t:   dump thread list<br>
       v:   dump thread stack<br>
       x:   clear classloader cache<br>
       0-5: set trace level to &lt;n&gt;<br>
       ----------------------------------------------------<br>
       Oct 19, 2013 1:40:05 AM qz.LogIt log<br>
       INFO: QZ-PRINT 1.6.8<br>
       Oct 19, 2013 1:40:05 AM qz.LogIt log<br>
       INFO: ===== JAVASCRIPT LISTENER THREAD STARTED =====<br>
       Oct 19, 2013 1:40:09 AM qz.LogIt log<br>
       INFO: ===== SEARCHING FOR PRINTER =====<br>
       Oct 19, 2013 1:40:10 AM qz.LogIt log<br>
       INFO: Found 4 attached printers.<br>
       Oct 19, 2013 1:40:10 AM qz.LogIt log<br>
       INFO: Printer specified: \QZebra\E<br>
       Oct 19, 2013 1:40:10 AM qz.LogIt log<br>
       INFO: Printer name match: \\myserver\Zebra LP2844<br>
       Oct 19, 2013 1:40:10 AM qz.LogIt log<br>
       INFO: Using best match: \\myserver\Zebra LP2844<br>
       Oct 19, 2013 1:40:10 AM qz.LogIt log<br>
       WARNING: Tried calling JavaScript function "jzebraDoneFindingPrinters" through web browser but it has not been implemented (No such method "jzebraDoneFindingPrinters" on JavaScript object)<br>
       CacheEntry[file:/C:/Users/Owner/Desktop/dist/qz-run.jnlp]: updateAvailable=false,lastModified=Sat Oct 19 01:27:44 EDT 2013,length=599<br>
       CacheEntry[file:/C:/Users/Owner/Desktop/dist/qz-print.jar]: updateAvailable=false,lastModified=Sat Oct 19 01:27:44 EDT 2013,length=105639<br>
       CacheEntry[file:/C:/Users/Owner/Desktop/dist/lib/jssc_qz.jar]: updateAvailable=false,lastModified=Sat Oct 19 01:27:44 EDT 2013,length=158623<br>
       CacheEntry[file:/C:/Users/Owner/Desktop/dist/lib/pdf-renderer_qz.jar]: updateAvailable=false,lastModified=Sat Oct 19 01:27:44 EDT 2013,length=1639200<br>
</code></pre></b>
<blockquote><tr><td> At this point, your applet has now been loaded into the web browser.  See Printing section for printer discovery and for sending print commands directly to your printer.                                                                           </td></tr></blockquote></li></ol></tbody></table>

<h2>Printing</h2>
<ol><li>qz-print's parameters are set through JavaScript commands.<br>
</li><li>First, insert (or modify) the JavaScript code to search for a printer named "zebra".  The printer name can be anything you wish, i.e: <code>"Epson"</code>, <code>"Citizen"</code>, <code>"Generic"</code>, <code>"BOCA"</code>, etc.<br>
<pre><code>      &lt;script&gt;<br>
      function findPrinter() {<br>
         // Searches for locally installed printer with "zebra" in the name<br>
         qz.findPrinter("zebra");<br>
<br>
         // *Note, to get the default printer, call:<br>
         // qz.findPrinter(); // or<br>
         // qz.findPrinter(null);<br>
      }<br>
      &lt;/script&gt;<br>
</code></pre>
<blockquote><table><thead><th> See also <code>sample.html</code>, section "findPrinter()". </th></thead><tbody>
<tr><td> <b>Note:</b> To select another printer, you can also choose it by index using <code>applet.setPrinter(index);</code> </td></tr>
</blockquote></li><li>Second, use html code for a <b>Find Printer</b> button using standard HTML input button.  This button has already been provided in <code>sample.html</code>.<br>
<pre><code>      &lt;input type=button onClick="findPrinter()" value="Detect Printer"&gt;&lt;br&gt;&lt;br&gt;<br>
</code></pre>
</li><li>Third, test the <b>Find Printer</b> button.<br>
<ul><li>Load page in web browser and click "Find Printer" button.<br>
</li><li>View Java console for output.  Look for <code>"INFO: Printer found..."</code>
</li><li><b>TODO:  Find Printer Button Screenshot</b>
</li></ul></li><li>Fourth, insert (or modify) this JavaScript code to send commands to printer. This button has already been provided in <code>sample.html</code>.<br>
<ul><li>JavaScript Code: (Example)<br>
<pre><code>      function print() {<br>
         // Send characters/raw commands to applet using "append"<br>
         // Hint:  Carriage Return = \r, New Line = \n, Escape Double Quotes= \"<br>
         qz.append("A37,503,0,1,2,3,N,QZ-PRINT TEST PRINT\n");<br>
<br>
         // Send characters/raw commands to printer<br>
         qz.print();<br>
      }<br>
</code></pre>
<blockquote><tr><td> See also <code>sample.html</code>, section "print()".       </td></tr>
</blockquote></li></ul><blockquote><tr><td> <b>Note:</b> The raw commands provided in the sample are not intended for use with your printer, they're provided as an example. </td></tr>
</blockquote></li><li>Next, add html code for a <b>Print</b> button. This button has already been provided in <code>sample.html</code>.<br>
<pre><code>       &lt;input type=button onClick="print()" value="Print"&gt;&lt;br&gt;&lt;br&gt;<br>
</code></pre>
</li><li>Last, test "print.html"<br>
<ul><li>Load page in web browser and click "Find Printer" button<br>
</li><li>Click "Print" button<br>
</li><li><b>TODO:  Print Button Screenshot</b>
</li><li><b>TODO:  Console Output Screenshot</b>
</li><li>View Java console for output<br>
</li></ul></li><li>If problems exist, try the included <b>sample.html</b> or email the <a href='mailto:tres.finocchiaro@gmail.com'>author</a>.</li></ol></tbody></table>

<h3>php Printing</h3>
<ol><li>If you would rather use php, replace <code>print()</code> function with this code:<br>
<pre><code>      function print() {<br>
         // Uses the php `"echo"` function in conjunction with qz-print `"append"` function<br>
         // This assumes you have already assigned a value to `"$commands"` with php<br>
         qz.append(&lt;?php echo $commands; ?&gt;);<br>
<br>
         // Send characters/raw commands to printer<br>
         qz.print();<br>
      }<br>
</code></pre></li></ol>

<h3>Base64 Printing</h3>
<ol><li>Note:  For Base64 image printing, see <a href='TutorialWebApplet#Printing_Images.md'>TutorialWebApplet#Printing_Images</a>
</li><li>If print data is base64 encoded, replace <code>print()</code> function with this code: (Note:  Versions 1.4.1 & 1.4.2 have a bug, see <a href='https://code.google.com/p/jzebra/issues/detail?id=73'>Issue 73</a>.)<br>
<pre><code>      // Use qz-print's `"append64"` function. This will automatically convert provided<br>
      // base64 encoded text into ascii/bytes, etc.<br>
      function print() {<br>
         qz.append64("SEVMTE8hICBZT1UgQVJFIFJFQURJTkcgQSBERUNPREVE");<br>
         qz.append64("IEJBU0U2NCBNRVNTQUdFIFNFTlQgRlJPTSBKWkVCUkEu");<br>
<br>
         // Send characters/raw commands to printer<br>
         qz.print();<br>
      }<br>
</code></pre>
<blockquote><table><thead><th> See also <code>sample.html</code>, section "print()". </th></thead><tbody></blockquote></li></ol></tbody></table>

<h3>Epson/Citizen ESC/P Printing</h3>
<blockquote><table><thead><th> <b>Note:</b> See <a href='ESCPCommands.md'>ESCPCommands</a> for many more examples </th></thead><tbody>
</blockquote><ol><li>Optional CHR() function for easier reading<br>
<pre><code>        function chr(i) {<br>
              return String.fromCharCode(i);<br>
        } <br>
</code></pre>
</li><li>Open cash drawer (usually connected to printer via cable)<br>
<pre><code>        function openCashDrawer() {<br>
              qz.append(chr(27) + "\x70" + "\x30" + chr(25) + chr(25) + "\r");<br>
              qz.print();<br>
        }<br>
</code></pre>
</li><li>Cut paper<br>
<pre><code>        function cutPaper() {<br>
              qz.append(chr(27) + chr(105));       // cut paper<br>
        }<br>
</code></pre>
</li><li>Basic font styling<br>
<pre><code>        function boldAndCenter() {<br>
             qz.append(chr(27) + chr(69) + "\r");  // bold on<br>
             qz.append(chr(27) + "\x61" + "\x31"); // center justify<br>
        }<br>
</code></pre>
</li><li>Print Image (Still experimental, needs testing)<br>
<blockquote>See <a href='TutorialWebApplet#Printing_Images.md'>TutorialWebApplet#Printing_Images</a></blockquote></li></ol></tbody></table>

<h3>Printing Special Characters</h3>
<ol><li>If special ascii, chr, hex or escape characters need to be printed, use the char code, or the "\x" notation.  Note, the "NUL" character, or "\x00" is not supported in JavaScript, so appendHex() is needed.<br>
<pre><code>      function print() {<br>
         // Appends CHR(27) + CHR(29) using `"fromCharCode"` function<br>
         qz.append(String.fromCharCode(27) + String.fromCharCode(29));<br>
<br>
         // Appends hexadecimal data<br>
         qz.appendHex("x00x01x02xFF");<br>
<br>
         // Send characters/raw commands to printer<br>
         qz.print();<br>
      }<br>
</code></pre>
<blockquote><table><thead><th> See also <code>sample.html</code>, section "print()". </th></thead><tbody>
<pre><code>       // Force special DOS/Win characters on UNIX/Linux<br>
       qz.setEncoding("cp866");       // or<br>
       qz.setEncoding("cp1252");<br>
<br>
       // Force UTF8 characters on Windows<br>
       qz.setEncoding("UTF-8");<br>
<br>
       // Force MS/DOS Western Europe  (i.e. "Maçã")<br>
       qz.setEncoding("850");<br>
</code></pre>
<tr><td> See also <a href='https://code.google.com/p/jzebra/issues/detail?id=28'>Issue 28</a> </td></tr>
<pre><code>       // Submitted via Simon on mailing list jzebra-users@googlegroups.com<br>
       // Print GBP '£' sign using ESC/P<br>
       // First change code page to UK<br>
       qz.appendHex("x1Bx52x03");<br>
       // Then just use '#' where you want your E<br>
       qz.append("#5.00");<br>
</code></pre>
<tr><td> See also <a href='https://code.google.com/p/jzebra/issues/detail?id=61'>Issue 61</a>, which also prevents append("\x00") from working. (Using appendHex() fixes this or many choose to use use Base64 encoded print commands </td></tr></blockquote></li></ol></tbody></table>

<h3>Advanced Print Spooling</h3>
<ol><li>Since version 1.0.6, qz-print has the ability to control spooling to the printer.  This feature allows to print in batches of 5, 10, etc.  This has advantages due to buffer limitation on certain printer models where submitting 100+ labels randomly stop in the middle of printing.  In addition, some programmers have had success with using it for easier reprints.<br>
<pre><code>      function print() {<br>
<br>
         // Mark the end of a label, in this case  P1 plus a newline character<br>
         // qz-printknows to look for this and treat this as the end of a "page"<br>
         // for better control of larger spooled jobs (i.e. 50+ labels)<br>
         qz.setEndOfDocument("P1\n");<br>
           <br>
         // The amount of labels to spool to the printer at a time. When<br>
         // qz-print counts this many `EndOfDocument`'s, a new print job will <br>
         // automatically be spooled to the printer and counting will start<br>
         // over.<br>
         qz.setDocumentsPerSpool("10");      <br>
<br>
         // Send characters/raw commands to printer<br>
         qz.print();<br>
      }<br>
</code></pre></li></ol>

<blockquote><table><thead><th> See also <code>sample.html</code>, section "printPages()". </th></thead><tbody></blockquote></tbody></table>

<h3>File Printing</h3>
<ol><li>This feature allows a raw file to be spooled directly to the printer<br>
<pre><code>    function printFile() {<br>
      	    if (qz != null) {<br>
	       // Using qz-print's "appendFile()" function, a file containg your raw EPL/ZPL<br>
	       // can be sent directly to the printer<br>
	       // Example: <br>
	       //     qz.appendFile("http://yoursite/zpllabel.txt"); // ...etc<br>
	       qz.appendFile(window.location.href + "/../zpl.txt");<br>
	       qz.print();<br>
	    }<br>
      }<br>
</code></pre></li></ol>

<h3>XML Printing</h3>

<ol><li>Since version 1.0.8, qz-print has the ability to read the contents of an XML file containing Base64 encoded commands and send these commands to the printer. The function requires two parameters, the URL of the XML file and the tagname containing the Base64 encoded text.<br>
<pre><code>      function printXML() {<br>
         // Appends the contents of an XML file from a SOAP response, etc.<br>
         // a valid relative URL or a valid complete URL is required for the XML<br>
         // file.  The second parameter must be a valid XML tag/node containing<br>
         // base64 encoded data, i.e. &lt;node_1&gt;aGVsbG8gd29ybGQ=&lt;/node_1&gt;<br>
         // Example:<br>
         //     qz.appendXML("http://yoursite.com/zpl.xml", "node_1");<br>
         qz.appendXML("C:\\zpl.xml", "v7:Image");<br>
<br>
         // Send characters/raw commands to printer<br>
         qz.print();<br>
      }<br>
<br>
</code></pre></li></ol>

<blockquote><table><thead><th> See also <code>sample.html</code>, section "printXML()". </th></thead><tbody></blockquote></tbody></table>

<h3>Print to File</h3>
<ol><li>Since version 1.1.9, qz-print allows printing to a physical file.  This is useful for bypassing printer drivers completely and sending raw data to a remote Windows Print Server queue, i.e. \\server\printer. (Thanks André T)<br>
<pre><code>      function printToFile() {<br>
         // Append some data<br>
         qz.append("A37,503,0,1,2,3,N,ABC WIDGET CO\n");<br>
<br>
         // Note, the doubly escaped forward slashes!<br>
         qz.printToFile("\\\\server\\printer")<br>
      }<br>
<br>
</code></pre></li></ol>

<h3>PDF Printing</h3>
<ol><li>Since version 1.1.9, qz-print allows printing PDF files directly to a printer.  This functionality is experimental and uses a 3rd party renderer "PDF-RENDERER".  <b>This feature will not work with many raw printing devices, such as Zebra, Epson, Citizen printers.  The data is sent in PostScript format, which is more common for LaserJet printers. USE WITH CAUTION!</b>
<pre><code>      function printPDF() {<br>
         // Make sure pdf-renderer.jar is in the "./lib" folder<br>
         // Append the PDF<br>
         qz.appendPDF(window.location.href + "/../sample.pdf");<br>
<br>
         // Very important for PDFs, use "printPS()" instead of "print()"<br>
         qz.printPS();<br>
      }<br>
</code></pre>
<blockquote><table><thead><th> <b>Note:</b> If printing dynamically generated PDF from php, make sure to add header <code>'Content-Type: application/pdf'</code> as well as <code>'Content-Disposition:inline;filename=example.pdf'</code> or else PDF-RENDERER plugin will throw an error: "Exception occurred: This may not be a PDF File".  See <a href='https://code.google.com/p/jzebra/issues/detail?id=48'>Issue 48</a> for more details </th></thead><tbody>
<tr><td> <b>CUPS/Linux PDF Printing:</b>  Please note, there is a bug preventing margins from working properly on some versions of CUPS: <a href='http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6726691'>http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6726691</a>                                                                                                                                              </td></tr></blockquote></li></ol></tbody></table>

<h3>Printing Images</h3>
<ol><li>Experimental support for appending printer-specific images by url and/or Base64.<br>
<pre><code>      // *Note 1:  Applet will append special raw markup, i.e. ^GFA, char(27), etc<br>
      // *Note 2:  Image width and image height must be divisible by 8<br>
      // *Note 3:  Newline/Carriage Return must be appended manually<br>
      // *Note 4:  Images should be strictly black and white<br>
<br>
      // Zebra (EPL):<br>
      qz.appendImage("image.png", "EPL");<br>
      while (!qz.isDoneAppending()) {} // wait<br>
      qz.append("\r\n");          <br>
<br>
      // Zebra (ZPLII):<br>
      qz.appendImage("image.png", "ZPLII");<br>
      while (!qz.isDoneAppending()) {} // wait<br>
      qz.append("\r\n");  <br>
<br>
      // Zebra (CPCL):<br>
      qz.appendImage("image.png", "CPCL");<br>
      while (!qz.isDoneAppending()) {} // wait<br>
      qz.append("\r\n");    <br>
<br>
      <br>
<br>
<br>
      // Epson (ESCP):<br>
      qz.appendImage("image.png", "ESCP");<br>
      while (!qz.isDoneAppending()) {} // wait<br>
      qz.append("\r\n");<br>
<br>
      // Base64<br>
      qz.appendImage("data:image/png;base64,AAAAAAAAA...", "ZPLII");<br>
      qz.append("\n");<br>
<br>
      // DeskJet/LaserJet, etc (don't mix with raw devices)<br>
      // Paper size/orientation since version 1.4.5<br>
      qz.setPaperSize("210mm", "297mm");  // A4<br>
      // qz.setPaperSize("8.5in", "11.0in");  // US Letter<br>
      qz.setAutoSize(true);               // Preserve proportions<br>
      qz.setOrientation("landscape");     // Default is "portrait"<br>
      qz.appendImage("image.png");        // Append our image.  Note: Wait for this to finish, or implement "jzebraDoneAppending()"<br>
      qz.print();<br>
</code></pre></li></ol>

<h3>HTML Printing</h3>
<ol><li>Since version 1.4.5, qz-print can print advanced HTML components by rendering an HTML component to an image using the html2canvas jQuery plugin (bundled in the /dist/js folder).<br>
<pre><code>       // HTML<br>
       &lt;body id="content" bgcolor="#FFF380"&gt; ... <br>
       &lt;canvas id="hidden_screenshot" style="display:none;" /&gt; ...<br>
<br>
       // JavaScript (jQuery)<br>
       $("#content").html2canvas({ <br>
                canvas: hidden_screenshot,<br>
                onrendered: function() {<br>
                   qz.append64($("canvas")[0].toDataURL('image/png'));<br>
                   qz.printPS();<br>
                }<br>
           });<br>
</code></pre></li></ol>

<blockquote><table><thead><th> <b>Note:</b> HTML id <code>#content</code> can be virtually any HTML component.  HTML id <code>hidden_screenshot</code> is a temporary place to draw the content and should be set <code>display=none</code> to prevent the render from becoming visiable. </th></thead><tbody></blockquote></tbody></table>

<ol><li>Since version 1.3.2, qz-print has the ability to print basic HTML components to a PostScript style printer directly from the browser.  (PostScript printers include all major LaserJet, DeskJet, PSC, Home Printers, etc).  Mileage may vary across different operating systems.  Please file a bug report using ISSUES link above if you encounter issues.<br>
<pre><code>      // Basic HTML Printing<br>
      qz.appendHTML("&lt;html&gt;&lt;h1&gt;&lt;font color=Red&gt;Hello world!&lt;/font&gt;&lt;/h1&gt;qz-print HTML Printing Demo&lt;/html&gt;");<br>
      qz.printHTML();<br>
<br>
<br>
<br>
<br>
      // Printing using extra spaces, fixed font, dashes<br>
      var text = "*no-line-break*       Hello from ’qz-print’       *no-line-break*";<br>
<br>
      // Fix whitespace and special character behavior<br>
      text = text.replace(/ /g, "&amp;nbsp;").replace(/’/g, "'").replace(/-/g,"&amp;#8209;");      <br>
<br>
      qz.appendHTML('&lt;html&gt;&lt;table border=1 style="font-size:10pt; font-face:\'Courier New\';"&gt;&lt;tr&gt;&lt;td&gt;' + text + '&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/html&gt;');<br>
<br>
      qz.printHTML();<br>
<br>
<br>
<br>
<br>
      // Printing an existing HTML file<br>
      qz.appendHTMLFile("../form.html");<br>
<br>
      // Wait for append to finish<br>
      while (!qz.isDoneAppending()) { // wait }<br>
<br>
      qz.printHTML();<br>
</code></pre>
<blockquote><table><thead><th> </th><th> <b>Linux HTML Printing:</b>  Please note, there is a bug preventing margins from working properly on Linux: <a href='http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6726691'>http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6726691</a> </th></thead><tbody></blockquote></li></ol></tbody></table>

<h3>Experimental / Work Arounds</h3>
<ol><li>Since version 1.4.6, An OSX-only work-around was added to qz-print that allows printing through CUPS command line (<code>lp -o raw</code>), <a href='https://code.google.com/p/jzebra/issues/detail?id=87'>Issue 87</a>.<br>
<pre><code>      // Alternate OSX raw printing via CUPS<br>
      qz.useAlternatePrinting(true);<br>
</code></pre></li></ol>

<h2>Serial Communication</h2>
<ol><li>Since version 1.6.0, You can send and receive data using the jSSC plugin (requires /dist/lib/jssc_qz.jar).<br>
<pre><code>      // List serial ports<br>
      qz.findPorts();<br>
<br>
      function jzebraDoneFindingPorts() {<br>
         var ports = qz.getPorts().split(",");<br>
	 for (p in ports) {<br>
	    alert(ports[p]);<br>
	 }<br>
      }<br>
<br>
 <br>
      // Open a serial port<br>
      qz.openPort("COM1"); //Can be dev/ttyS0, /dev/ttyUSB0, depending on platform<br>
      <br>
      function jzebraDoneOpeningPort(portName) {<br>
         alert("Port [" + portName +  "] is open!");<br>
      }<br>
<br>
<br>
      // Send serial data<br>
      // Beggining and ending patterns that signify port has responded<br>
      // chr(2) and chr(13) surround data on a Mettler Toledo Scale<br>
      qz.setSerialBegin(chr(2));<br>
      qz.setSerialEnd(chr(13));<br>
      // Baud rate, data bits, stop bits, parity, flow control<br>
      // "9600", "7", "1", "even", "none" = Default for Mettler Toledo Scale<br>
      qz.setSerialProperties("9600", "7", "1", "even", "none");<br>
      // Send raw commands to the specified port.<br>
      // W = weight on Mettler Toledo Scale<br>
      qz.send(document.getElementById("port_name").value, "\nW\n");<br>
      <br>
      <br>
      // Retrieve serial response (automatically called)<br>
      function jzebraSerialReturned(portName, data) {<br>
         alert("Port [" + portName + "] returned data:\n\t" + data);<br>
      }<br>
      <br>
       <br>
      // Close a serial port<br>
      qz.closePort("COM1"); //Can be dev/ttyS0, /dev/ttyUSB0, depending on platform<br>
      <br>
      function jzebraDoneClosingPort(portName) {<br>
         alert("Port [" + portName +  "] is open!");<br>
      }<br>
      <br>
</code></pre></li></ol>

<h3>End of Tutorial</h3>

<h2>Conclusion</h2>
<blockquote>This tutorial needs work.  Please help by submitting changes.  Email questions or suggestions to <a href='mailto:tres.finocchiaro@gmail.com'>the author</a>.</blockquote>

Alternatively, For questions, feedback and updates, subscribe to the <b>qz-print Mailing List</b> on Google Groups:<br>
<blockquote><a href='http://groups.google.com/group/jzebra-users'><img src='http://groups.google.com/intl/en/images/logos/groups_logo_sm.gif' /></a>