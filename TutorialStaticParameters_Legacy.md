| <img src='http://img413.imageshack.us/img413/4710/firefox2ie7nn0.gif' align='middle'> <a href='TutorialWebApplet_Legacy.md'>Web Applet</a> <table><thead><th> <img src='http://4.bp.blogspot.com/_9hmP3Ho0t14/Sveb2dQ1H6I/AAAAAAAAAV4/-f-r_lZzLWQ/s400/Properties-48x48.png' align='middle'> <b><a href='TutorialStaticParameters_Legacy.md'>Common Parameters</a></b> </th></thead><tbody></tbody></table>

<h1>Introduction</h1>

<b>This tutorial is for an old version. For the latest version, please see <a href='TutorialWebApplet.md'>TutorialWebApplet</a></b>

jZebra takes a number of <b>Static Parameters</b> that vary slightly between usage.  For example, messages representing print status, such as success messages, error messages or suppressing messages are all set through parameters prior to loading jZebra.  Their default values will change between usage.  Parameters that don't apply to a specific print mode are marked as "<code>&lt;n/a&gt;</code>" and can be ignored.<br>
<br>
<hr />

<h1>Static Parameters</h1>
<table><thead><th> </th><th> </th><th> <b>Web Applet Default</b> </th><th> <b>Desktop App Default</b> </th><th> <b>Console App Default</b> </th></thead><tbody>
<tr><td> <h3>Parameter</h3> </td><td> <h3>Description</h3>  </td><td> <img src='http://img413.imageshack.us/img413/4710/firefox2ie7nn0.gif' /> </td><td> <img src='http://img413.imageshack.us/img413/9843/toggledesktopes0.png' /> </td><td> <img src='http://img413.imageshack.us/img413/6632/terminal1mq3.png' /> </td></tr>
<tr><td> <code>AUTOPRINT</code> </td><td> Automatically prints once jZebra is finished loading. </td><td> <code>"true"</code>       </td><td> <code>"false"</code>       </td><td> <code>"true"</code>        </td></tr>
<tr><td> <code>SUCCESSMESSAGE</code> </td><td> The message to display after a successful print.  Allows html text formatting. <td><code>"jZebra has successfully &lt;...&gt;"</code></td> </td></tr>
<tr><td> <code>ERRORMESSAGE</code> </td><td> The message to display after a failed print.  Allows html text formatting. <td><code>"jZebra encountered and error &lt;...&gt;"</code></td> </td></tr>
<tr><td> <code>MESSAGETITLE</code> </td><td> The title bar text at the top of message dialogs. </td><td> <code>"jZebra"</code>     </td><td> <code>"jZebra"</code>      </td><td> <code>&lt;n/a&gt;</code>   </td></tr>
<tr><td> <code>SHOWMESSAGES</code> </td><td> When set to false, suppresses both success and error messages from displaying on the screen. </td><td> <code>"true"</code>       </td><td> <code>"true"</code>        </td><td> <code>&lt;n/a&gt;</code>   </td></tr>
<tr><td> <code>CONFIGTYPE</code> </td><td> The raw file source type: <img src='http://img181.imageshack.us/img181/6414/fileav5.png' /><b><code>FILE</code></b>, <img src='http://img181.imageshack.us/img181/1514/urlcd6.png' /><b><code>URL</code></b>, <img src='http://img181.imageshack.us/img181/8660/resourcefv2.png' /><b><code>RESOURCE</code></b> </td><td> <img src='http://img181.imageshack.us/img181/1514/urlcd6.png' /><code>"url"</code> </td><td> <img src='http://img181.imageshack.us/img181/6414/fileav5.png' /><code>"file"</code> </td><td> <img src='http://img181.imageshack.us/img181/6414/fileav5.png' /><code>"file"</code> </td></tr>
<tr><td> <code>CONFIGPATH</code> </td><td> The path (<code>http://</code>, <code>C:\</code>, <code>/home/user/</code>, etc) to the raw file containing the print commands. <td><code>"/jzebra/resources/commands.txt"</code></td> </td></tr>
<tr><td> <code>LINEFEED</code> </td><td> The linefeed character(s) to send after each new line in the config file. </td><td> <code>"\n"</code>         </td><td> <code>"\n"</code>          </td><td> <code>"\n"</code>          </td></tr>
<tr><td> <code>BUTTONTEXT</code> </td><td> The text to be displayed on the print button. </td><td> <code>"Print"</code>      </td><td> <code>"Print"</code>       </td><td> <code>&lt;n/a&gt;</code>   </td></tr>
<tr><td> <code>SHOWICON</code> </td><td> When set to false, removes the print image from the print button. </td><td> <code>"true"</code>       </td><td> <code>"true"</code>        </td><td> <code>&lt;n/a&gt;</code>   </td></tr></tbody></table>


<hr />

<table><thead><th> <h3>Important</h3>The <b><code>"CONFIGTYPE"</code></b> parameter will default to <img src='http://img181.imageshack.us/img181/8660/resourcefv2.png' /><b><code>"RESOURCE"</code></b> if <b><code>"CONFIGPATH"</code></b> is not defined. </th></thead><tbody>