# Installing Java #
jZebra requires **Java Runtime 5** or higher to load.  This is also named: "**`java version '1.5.x_x'`**", "**`J2SE 5.0`**", "**`JRE 5.0`**", or "**`JDK 5.0`**".

---


  1. Check for Java by typing the following at a command console:
```
  java -version
```
  1. This should return the following:
```
  java version "1.x.x_xx"
  Java(TM) SE Runtime Environment (build 1.x.x_xx-xxx)
  Java HotSpot(TM) Client VM (build xx.x-xxx, mixed mode, sharing)
```
  1. If "**`java version '1.5.0_0'`**" or higher does not appear to be installed, download and install the [Java Runtime Environment](http://www.java.com/getjava/) for your platform.  This varies with your platform:
    * **Windows** users, download from the **Java link above**.
    * **Ubuntu** users, see here:  https://help.ubuntu.com/community/Java
    * **Linux** users, download from repository (**apt-get**, **yum**, etc.  Look for "**sun-jre**" or "**OpenJDK**" and appropriate browser plugins).  Browser plugin may be called "icedtea" and is often a separate install.  KDE users may also need to install "xul-runner".
    * **Mac** users previously obtained java through **automatic updates**.  Newer versions of Java (1.7 and later) need to be downloaded and installed separately here: http://www.oracle.com/technetwork/java/javase/downloads