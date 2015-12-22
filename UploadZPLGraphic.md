Printer Model: Zebra S4M

First problem: I would like to send raw commands to the printer via browser
| **Solution:** Use jZebra |
|:-------------------------|

Second problem: How can I print images?
| **Solution:** First of all you need to upload your image to the printer’s memory, so you can call it back. |
|:-----------------------------------------------------------------------------------------------------------|

Third problem: The easiest way to upload an image to the printer is via Zebra’s Software.

| A brief explanation: Reading the manual, you’ll see that before you upload any image, you need to convert the normal image (.png .jpg….) to hexadecimal, and handle with a lot of bytes, than you upload this bytes.<br><br>Also you have 3 options to store your image, the first one is to upload your image to a volatile memory, which is erased when the printer shutdown. The second is store it in a flash drive (this is what I did, and works fine to me), and just call it from your code. The last one is write a “script” which is executed in every printer's boot, this script should be stored in a flash drive too. </tbody></table>

| **Solution:** I used the second solution because I didn’t want to handle with a lots of bytes. The steps is very easy and anyone can do it: |
|:--------------------------------------------------------------------------------------------------------------------------------------------|

  1. Open Zebra Setup Utilities > double-click in your printer
  1. Switch to tab named Printer Memory, in section “Flash” select “Memory Card”, and in Connected File select MSung or any other with sufficient space. Then click in OK.
  1. Click in Download Fonts and Graphics > Card > Printer Selection > and select your printer.
  1. In Memory Card Slot select “Flash”.
  1. Now, in Pictures > Add, choose your image. Next you’ll prompted if you want to download that image, click in YES, it will upload your image to printer’s memory.
  1. Now you are able to call your image from the source! Here is an example:

|`^XA`<br><code>^FT</code><font color='red'><code>32,128</code></font><code>^XG</code><font color='blue'><code>MYIMAGE.GRF</code></font><code>,1,1^FS</code><br><code>^XZ</code> <br><br><b>Note:</b> Programming Language: ZPLII </tbody></table>

<ul><li><font color='red'>Numbers in red means the coordinates where the image will start to be print.</font></li></ul>

<ul><li><font color='blue'>The text in blue is your image name. (.GRF is the extension, my image was a MYIMAGE.png, but Zebras’ Software will automatically do the conversion for you, so forget the hexadecimal and the bytes!)</font></li></ul>

-Bruno