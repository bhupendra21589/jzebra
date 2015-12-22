f#summary Change security prompt to verified or change the digital signature publisher name

# <font color='red'>Please see updated tutorial here: <a href='https://github.com/qzindustries/qz-print/wiki/Compile-qz-print'>https://github.com/qzindustries/qz-print/wiki/Compile-qz-print</a></font> #
# Objective #

Fix "digital signature cannot be verified" message that appears when running jZebra signed applet.  This is done by recompiling jZebra with NetBeans, and replacing the digital certificate with your company's certificate.

> | **Note:** Estimated time to complete: 2 hours |
|:----------------------------------------------|

# Prerequisites #

  1. This tutorial assumes web server is running Linux or BSD. It can be adapted for others but mileage may vary.  If the certificate is already formatted for Java and being installed on a PC, then some of these "server" steps can be skipped/performed on via PC command line.
  1. Web server should have Java installed.  If not, "keytool" steps will need to be performed on workstation instead.
  1. Need console access to the web server running OpenSSL
  1. Putty (or equivalent) installed, WinSCP (or equivalent) installed
  1. Must have an OpenSSL private key used to obtain purchased signing certificate, example "MyCompany.cer"
  1. Must have a purchased signing certificate (i.e. Verisign, Thawte, Geotrust), example "CodeSigningCA.cer"
  1. Must have a root certificate from said company, example "PrimaryRootCA.cer"
  1. Installed and working Java JDK + NetBeans bundle (i.e. [NetBeans 7.0, JDK 1.6.x](http://www.oracle.com/technetwork/java/javase/downloads/jdk-netbeans-jsp-142931.html))
  1. Installed and working [JDK 1.5.x](http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html)

# Setup NetBeans #
  1. If not already, install the latest bundled version of Java Development Kit & NetBeans taking defaults. Registration is optional and can be skipped.
  1. Register the older 1.5 JDK using Tools, Java Platforms, Add, and navigate to C:\Program Files\Java\jdk1.5.0\_xx.
  1. Open the project in NetBeans using the following steps:
    * Download the latest [jZebra source](http://code.google.com/p/jzebra/downloads/)
    * Extract the contents to the NetBeans project folder (Usually "My Documents/NetBeansProjects", or "home/NetBeansProjects") in a folder called "jZebra"
    * With NetBeans open, import the project using File, Open and browse for the newly created "jZebra" folder.
    * In the top left "Projects" pane, you should see a red coffee cup with the word "jzebra" next to it.
> > > | **Note:**  If "Projects" does not appear in NetBeans, hit CTRL + 1 to make it visible. |
|:---------------------------------------------------------------------------------------|
    * If jzebra appears to be in error (exclamation mark), you may need to change the target platform to the correctly installed JDK: Right-click "jzebra", Properties, Libraries.  Click "JDK 1.5" (if installed) or "JDK 1.6 Default". Click OK. (Note: OpenJDK will work too, just use the equivalent commands/paths)







# Steps #

> | **Note:** Please adjust "mycompany" and "!mypassword!" appropriately to suit your needs.  Do not use spaces. |
|:-------------------------------------------------------------------------------------------------------------|
  1. Using Putty, connect to the web server console
  1. Create a directory on the web server, i.e. "/home/myuser/signing"
```
   $ mkdir ~/signing
```
  1. Using WinSCP, copy three signature files to the new directory on the web server (i.e: CodeSigningCA.cer, PrimaryRootCA.cer, MyCompany.cer)
  1. Using OpenSSL through Putty, convert the private key and the code sign cert to PCKS12 format:
```
   $ openssl pkcs12 -export -in MyCompany.cer -inkey mycompany.key -out mycompany.p12 -name "mycompany"
```
  1. Using Java keytool, convert the PCKS12 keystore into a JKS keystore:
```
   $ keytool -importkeystore -deststorepass !mypassword! -destkeypass !mypassword! -destkeystore keystore.jks -srckeystore mycompany.p12 -srcstoretype PKCS12 -srcstorepass !mypassword! -alias mycompany
```
  1. Subsequently, import the two intermediate certificates in the JKS keystore:
```
   $ keytool -import -trustcacerts -alias intca -file CodeSigningCA-G2.cer -keystore keystore.jks
   $ keytool -import -trustcacerts -alias crossca -file PrimaryRootCA.cer -keystore keystore.jks
```

| **Note:** At this moment, the keystore can be used to code sign, however the signing certificate is not correctly chained (most likely due to a final missing self-signed certificate from CA) and therefore the certificate issuer can not be successfully verified. |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

  1. Now follow exactly the process described at
[comodo.com](https://support.comodo.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=1221) ,
so that you end up with a PCKS12 formatted keystore with the fully chained certificate. Call it mycompany.p12 and protected it with the "!mypassword!" passphrase.

  1. Overwrite the code sign certificate in the JKS keystore with the fully chained version in the PKCS12 keystore:
```
   keytool -importkeystore -deststorepass !mypassword! -destkeypass !mypassword! -destkeystore keystore.jks -srckeystore mycompany.p12 -srcstoretype PKCS12 -srcstorepass !mypassword! -alias mycompany
```
  1. Answer "yes" to overwrite prompt:
```
   Existing entry alias mycompany exists, overwrite? [no]:  yes 
```

  1. Copy the keystore.jks keystore into the jZebra NetBeans
project and the jnlp-impl.xml (this location may have changed in newer versions, looks through the project xml files for "storepass") file with the ant recipes can be modified to sign using the correct keystore and alias:
```
   <target name="-jnlp-init-keystore1" if="generated.key.signing">
      <property name="jnlp.signjar.keystore" value="${basedir}/keystore.jks" />
      <property name="jnlp.signjar.storepass" value="!mypassword!"/>
      <property name="jnlp.signjar.keypass" value="!mypassword!"/>
      <property name="jnlp.signjar.alias" value="mycompany"/>
   </target>
```


# Keep #
  1. By default jZebra uses "jzebra.ks" for it's KeyStore.  To use an alternate KeyStore, drag it in to the "Files" panel.
> > | **Note:**  If "Files" does not appear in NetBeans, hit CTRL + 2 to make it visible. Alternately, you can copy it to "NetBeansProjects/jZebra" |
|:----------------------------------------------------------------------------------------------------------------------------------------------|
    1. The KeyStore requires four fields: A file name, a store password, a key password and an alias name to be entered.  The compiler will do this automatically so as long as the values are defined in "NetBeansProjects\jZebra\nbprojects\jnlp-impl.xml" as `jnlp.signjar.keystore`, `jnlp.signjar.storepass`, `jnlp.signjar.keypass`, `jnlp.signjar.alias` respectively.
> > > | **Note:** Be careful as not to break the formatting of the html file.                                                                         |
    1. Click the ![http://2.bp.blogspot.com/_9hmP3Ho0t14/S3CbTCYXxqI/AAAAAAAAAY4/AOvjXs3cgec/s400/Picture+10.png](http://2.bp.blogspot.com/_9hmP3Ho0t14/S3CbTCYXxqI/AAAAAAAAAY4/AOvjXs3cgec/s400/Picture+10.png) Hammer + Broom icon to do a clean build.
    1. Find your newly created and signed JAR file in your source folder in a folder called "dist" ("NetBeansProjects\jZebra\dist\jZebra.jar")
    1. Deploy the new jar to a test web location.
    1. Email jzebra-users@googlegroups.com with questions/comments in this process.






# Change Applet Branding #

If you are NOT using a [root certificate](http://en.wikipedia.org/wiki/Root_certificate) to sign jZebra it (Verisign, Thawte, etc), here are the steps to simply change the publisher name when prompted by the Security Dialog:

  1. Download the [latest version of Netbeans](http://netbeans.org/downloads/) (The **Java SE** version is sufficient).
  1. Install Netbeans taking defaults.  Registration is optional and can be skipped.
  1. Download the [latest source code](http://code.google.com/p/jzebra/downloads)
  1. Extract source to a folder.
  1. In Netbeans, click:  **Project --&gt; Open Project --&gt; &lt;browse to the extracted source code&gt;**  The icon should look like a red coffee cup.
  1. On the left "Projects" pane, **Right Click** the red coffee cup "jZebra" and click **Properties**
  1. Click **Application** from the list on the left.
  1. Change vendor from "Tres Finocchiaro" to &lt;Name of Company&gt; and click OK to close the dialog.
  1. Click the ![http://2.bp.blogspot.com/_9hmP3Ho0t14/S3CbTCYXxqI/AAAAAAAAAY4/AOvjXs3cgec/s400/Picture+10.png](http://2.bp.blogspot.com/_9hmP3Ho0t14/S3CbTCYXxqI/AAAAAAAAAY4/AOvjXs3cgec/s400/Picture+10.png) Hammer + Broom icon to do a clean build.
  1. Find your newly created and signed JAR file in your source folder in a folder called "dist".



-Tres


| Please choose your certificate provider wisely.  jZebra is not affiliated with Verisign or Thawte. |
|:---------------------------------------------------------------------------------------------------|