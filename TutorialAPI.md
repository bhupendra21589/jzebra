Introduction

This is Java code [snippet](http://en.wikipedia.org/wiki/Snippet_(programming)) that will allow you to use jZebra directly in your Java Application.

# Steps #
  1. Make sure [jzebra.jar](http://code.google.com/p/jzebra/downloads/list) is in your java class path.
  1. Make sure your printer is set up on your workstation with the name "`zebra`".  For step-by-step instructions:  [Windows](TutorialRawXP.md), [OS X](TutorialRawOSX.md), [Ubuntu](TutorialRawUbuntu.md)
  1. Adapt the following code to work in your Java project.
```
  import javax.print.PrintService;
  import java.lang.Exception;
  import jzebra.PrintRaw;
  import jzebra.PrintServiceMatcher;
  
  ...
  
  try {
     String rawCmds = "A37,503,0,1,2,3,N,\"ABC WIDGET CO\"";
     String printer = "zebra";  // This should match your printer name from Step 2
     PrintService ps = PrintServiceMatcher.findPrinter(printer);
     if (ps != null) {
        PrintRaw p = new PrintRaw(ps, rawCmds);
        return p.print();
     }
     else {
       System.err.println("Could not find printer!");
     }
    
  }
  catch (Exception e) {
     e.printStackTrace();
  }
```
  1. End of Steps