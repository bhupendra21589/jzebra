| <img src='http://img413.imageshack.us/img413/4710/firefox2ie7nn0.gif' align='middle'> <b><a href='TutorialWebApplet_Legacy.md'>Web Applet</a></b> <table><thead><th> <img src='http://4.bp.blogspot.com/_9hmP3Ho0t14/Sveb2dQ1H6I/AAAAAAAAAV4/-f-r_lZzLWQ/s400/Properties-48x48.png' align='middle'> <a href='TutorialStaticParameters_Legacy.md'>Common Parameters</a> </th></thead><tbody></tbody></table>

<h1>Introduction</h1>
This is a step-by-step tutorial that walks a web developer through creating a <b>basic html web applet</b> capable of sending raw commands directly to a printer.<br>
<br>
<b>This tutorial is for an old version.  For the latest version, please see <a href='TutorialWebApplet.md'>TutorialWebApplet</a></b>

For a quickstart,  download and extract the <a href='http://code.google.com/p/jzebra/downloads/list'>version 1.0.3_pre4</a> and examine the applet code inside the provide sample html.<br>
<br>
<blockquote><table><thead><th> <a href='http://2.bp.blogspot.com/_9hmP3Ho0t14/SveEeR-bCPI/AAAAAAAAAVo/6YIGLK_GGZo/s1600/xp_ie7.PNG'>http://2.bp.blogspot.com/_9hmP3Ho0t14/SveEeR-bCPI/AAAAAAAAAVo/6YIGLK_GGZo/s200/xp_ie7.PNG</a> </th></thead><tbody></blockquote></tbody></table>

<blockquote><table><thead><th> <b>Note:</b> jZebra requires Java 5 or higher to run.  For help installing Java on your platform, see the <img src='http://img132.imageshack.us/img132/3416/cup1ad7.png' /><a href='TutorialJavaInstall.md'>Java tutorial</a>. </th></thead><tbody></blockquote></tbody></table>

<hr />
<h1>Steps</h1>
<h2>Load The Applet</h2>
<ol><li>Make sure your printer is set up on your workstation with the name "zebra".  For step-by-step instructions:  <a href='TutorialRawXP.md'>Windows</a>, <a href='TutorialRawOSX.md'>OS X</a>, <a href='TutorialRawUbuntu.md'>Ubuntu</a>
</li><li>Download the legacy version <img src='http://img104.imageshack.us/img104/9696/packagept0.png' /><code>jZebra_1.0.3_pre4.zip</code> from <img src='http://img242.imageshack.us/img242/5678/diskmultiplebx6.png' /><a href='http://code.google.com/p/jzebra/downloads/list'>downloads</a> and extract the contents to your desktop.<br>
<ul><li>Make sure to extract the entire contents at once so that the folder and file structure stays in tact.<br>
</li><li>Locate the html sample file and open it with a text editor.  Windows users can use <b><img src='http://img174.imageshack.us/img174/2286/notepadle4.gif' />notepad</b>.  Linux users can use <b><img src='http://img174.imageshack.us/img174/6650/accessoriestexteditor16ol7.png' />gedit</b> (Ubuntu calls this "<b><img src='http://img174.imageshack.us/img174/6650/accessoriestexteditor16ol7.png' />Text Editor</b>").  This should be called "<img src='http://img74.imageshack.us/img74/2484/post997051213609968km7.png' /><code>preview-application.html</code>".  Look over the applet code quickly to get comfortable with the parameters.<br>
</li><li>Close out "<img src='http://img74.imageshack.us/img74/2484/post997051213609968km7.png' /><code>preview-application.html</code>" and use the same text editor to make a new file.  Start by inserting the code to create the applet.<br>
<pre><code>    &lt;html&gt;&lt;body&gt;<br>
       &lt;applet code="jzebra.JZebraApplet.class" archive="./jzebra.jar" width="200" height="25"&gt;<br>
          &lt;param name="buttontext" value="Sample button"&gt;<br>
       &lt;/applet&gt;<br>
    &lt;/html&gt;&lt;/body&gt;<br>
</code></pre>
</li><li>Save the file in the same folder as <img src='http://img104.imageshack.us/img104/9696/packagept0.png' /><code>jzebra.jar</code> and open the file with the browser of your choice.<br>
</li></ul><blockquote><table><thead><th> <b>Note:</b> IE7 may be prompt to "<a href='http://www.mix-fx.com/flash-prompt.htm'>Click to Activate This Control</a>" each time the applet loads. </th></thead><tbody>
<tr><td> <b>Note:</b> If you do not have a printer named "zebra" attached to your station, then you will have a <code>SEVERE: Printer not found</code> in your log.  To fix this, create printer "zebra" in the name.  Instructions: <a href='TutorialRawXP.md'>XP</a>, <a href='TutorialRawUbuntu.md'>Ubuntu</a>, <a href='TutorialRawOSX.md'>OS X</a> </td></tr>
<tr><td> <b>Note:</b> The raw commands provided in the sample are not intended for use with your printer, they're provided as an example.                    </td></tr>
</blockquote></li><li>The applet will begin to load in the web page.<br>
<blockquote><img src='http://img132.imageshack.us/img132/3484/javaloadingca2.png' />
</blockquote></li><li>Next, Java security dialog prompt is shown.  This is Java's way of warning that the Web Applet has access to local resources.  jZebra needs local access to the workstation's printers, so click "Run".<br>
<blockquote><img src='http://img132.imageshack.us/img132/6508/jzebrasecuritydialogip3.png' />
</blockquote></li><li>Your "Sample button" should have loaded.  If the browser stops responding or the applet never loads, check to make sure files were extracted correctly and that the archive is set properly in the html.<br>
</li><li>Click the "Sample button".  It will most likely do nothing, this is normal.  What is important is that the output is checked in the Java console. Windows users can enable this by right clicking the Java system tray icon and clicking "<a href='http://img74.imageshack.us/img74/2423/jzebrajava1tx5.png'>Open Java Console</a>".  Linux users, email <a href='mailto:tres.finocchiaro@gmail.com'>the author</a> if you've found a way to display a similar console.<br>
</li><li>The Java Console is critical for calibrating the applet for your printer.<br>
</li><li>If you already have a Zebra printer attached to your station, the applet will try to automatically use it by searching for the name "zebra" in all of your attached printers and will select the first match. Look for "INFO:  Printer found...". (This can later be changed using TutorialStaticParameters)<br>
<blockquote><img src='http://img518.imageshack.us/img518/4696/jzebraprinterfoundfb0.png' />
</blockquote></li><li>Look in the Java console log for something like the screenshot below.  You should see the default raw commands that jZebra ships with.  These will most likely look a bit foreign to you, that's normal.  The supplied commands are EPL commands.  We'll change them to something your printer can use in the steps following.<br>
<blockquote><img src='http://img443.imageshack.us/img443/2775/jzebrajava2gh7.png' /></blockquote></li></ol></tbody></table>

<h2>Set Parameters</h2>
<ol><li>Set the <code>LINEFEED</code> parameter based on your printer's programmer's guide.<br>
<ul><li>New Line Character<br>
<pre><code>       &lt;param name="linefeed" value="\n"&gt;<br>
</code></pre>
</li><li>New Line + Carriage Return<br>
<pre><code>       &lt;param name="linefeed" value="\r\n"&gt;<br>
</code></pre>
</li></ul></li><li>Set the <code>CONFIGPATH</code> parameter to point to a file with raw commands in it.<br>
<ul><li>Local File<br>
<pre><code>       &lt;param name="configpath" value="c:\test.txt"&gt;<br>
</code></pre>
</li><li>Web Hosted URL<br>
<pre><code>       &lt;param name="configpath" value="http://mysite/file1.raw"&gt;<br>
</code></pre>
</li></ul></li><li>Set the <code>CONFIGTYPE</code> parameter that matches what was used in Step 2.<br>
<ul><li>Local File<br>
<pre><code>       &lt;param name="configtype" value="file"&gt;<br>
</code></pre>
</li><li>Web Hosted URL<br>
<pre><code>       &lt;param name="configtype" value="url"&gt;<br>
</code></pre>
</li></ul></li><li>Make sure printer is connected as a raw print queue.<br>
<blockquote><a href='http://code.google.com/p/jzebra/wiki/TutorialRawXP#Steps'><img src='http://3.bp.blogspot.com/_9hmP3Ho0t14/SvXbFLIbfXI/AAAAAAAAAUQ/EmPDrWLk7YI/s400/config_win.png' /></a><a href='http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu#Steps'><img src='http://4.bp.blogspot.com/_9hmP3Ho0t14/SvXbE4Sp39I/AAAAAAAAAUI/dvvUZ_sJNQA/s400/config_lin.png' /></a><a href='http://code.google.com/p/jzebra/wiki/TutorialRawOSX#Steps'><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvXbE_kTK_I/AAAAAAAAAUA/a-Ucl9UaIvI/s400/config_mac.png' /></a><img src='http://2.bp.blogspot.com/_9hmP3Ho0t14/SvXbEnoMELI/AAAAAAAAAT4/eF4xkJ68ALY/s400/config_end.png' />
</blockquote></li><li>Load the applet and try to print.</li></ol>

<h3>Command Substitution</h3>
<ol><li>jZebra allows any word in a raw print file to be replaced through applet code by using a dollar sign <code>$</code>.  This will treat the raw file as a template.<br>
<ul><li>Original<br>
<pre><code>   A37,503,0,1,2,3,N,"ABC WIDGET CO"<br>
   A37,545,0,1,2,3,N,"1234 LIMBO STREET"<br>
   A37,587,0,1,2,3,N,"**TEST LABEL - DO NOT SHIP**"<br>
   A37,629,0,1,2,3,N,"AKRON OH 44333"<br>
   A37,461,0,1,2,3,N,"JOE CUSTOMER"<br>
   A35,671,0,2,1,1,N,"(330) 555-1234"<br>
</code></pre>
</li><li>Substitution<br>
<pre><code>   A37,503,0,1,2,3,N,"$BUSINESS"<br>
   A37,545,0,1,2,3,N,"$ADDRESS"<br>
   A37,587,0,1,2,3,N,"$MESSAGE"<br>
   A37,629,0,1,2,3,N,"$CITYSTATEZIP"<br>
   A37,461,0,1,2,3,N,"$NAME"<br>
   A35,671,0,2,1,1,N,"$PHONE"<br>
</code></pre>
</li><li>Additional HTML<br>
<pre><code>   &lt;param name="BUSINESS" value="ABC WIDGET CO"&gt;<br>
   &lt;param name="ADDRESS" value="1234 LIMBO STREET"&gt;<br>
   &lt;param name="MESSAGE" value="**TEST LABEL - DO NOT SHIP**"&gt;<br>
   &lt;param name="CITYSTATEZIP" value="AKRON OH 44333"&gt;<br>
   &lt;param name="NAME" value="JOE CUSTOMER"&gt;<br>
   &lt;param name="PHONE" value="(330) 555-1234"&gt;<br>
</code></pre>
</li></ul></li><li>Second example:  Using the supplied example:<br>
<blockquote><img src='http://img443.imageshack.us/img443/3849/jzebracommandreplaceji3.png' />
<pre><code>      &lt;param name="FIRSTNAME" value="TRES"&gt;<br>
</code></pre>
<img src='http://img443.imageshack.us/img443/6216/jzebracommandreplace2jz6.png' />
<table><thead><th> <b>Note:</b> Dollar sign variables will be left verbatim if not supplied as applet parameters. </th></thead><tbody></blockquote></li></ol></tbody></table>

<h2>From php</h2>
<ol><li>Courtesy of James at Reason Transport<br>
<pre><code>   &lt;applet code="jzebra.JZebraApplet.class" archive="&lt;?php echo $imgdir; ?&gt;/jzebra.jar" width="138" height="25"&gt;<br>
      &lt;param name="config" value="&lt;?php echo $depurl; ?&gt;/test"&gt;<br>
      &lt;param name="autoprint" value="true"&gt;<br>
      &lt;param name="printer" value="zebra"&gt;<br>
      &lt;param name="showicon" value="false"&gt;<br>
      &lt;param name="linefeed" value="\n"&gt;<br>
      &lt;param name="showmessages" value="false"&gt;<br>
   &lt;/applet&gt;<br>
</code></pre></li></ol>

<h2>Conclusion</h2>
<blockquote>Please email questions or suggestions to <a href='mailto:tres.finocchiaro@gmail.com'>the author</a>.