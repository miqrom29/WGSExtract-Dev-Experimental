# WGS Extract Betav2b MacOSX Patch File Instructions

In short: These are instructions to overlay the [MacOSX patch file](https://github.com/WGSExtract/WGSExtract-Dev/blob/master/WGSExtract_MacOSX_Patch.zip) 
onto your current [WGS Extract Betav2b release from 18 February 2020](https://github.com/WGSExtract/WGSExtract-Dev/blob/master/docs/README.md). 
For MacOSX only installations. 

In the Patch are two Applescript APPS that provide a GUI window click startup in the MacOS environment.
- a new **Install_MacOSX** app for MacOSX to do a proper environment install before you run the **WGS Exract** program. This installer acts as both an installer and updater.  You can run it again in the future to make sure the dependent tools are up to date. (It will not update **WGS Extract** itself, just the dependent tools.)
- a new, simple **Start_MacOSX** command to start **WGS Extract** more reliably. 

<ul>
<li>For compatability across all the recent MacOSX versions, we have made the underlying shell scripts rely on /bin/sh.  With MacOSX 10.15 Catalina, Apple has chosen to now give a warning when using any shell other than zsh. Please ignore this.  Everything is fine with /bin/sh and this provides compatability across release platforms. As it is, the warning is really about Apple changing the default from BASH to Zsh. It would be nice if Apple presented this warning only at login (or at least only once) and not every time you start a shell script.</li>
<li>The first time you run these apps, it will ask for permission to run **Terminal** inside them.  We use this so you have a command script log of what is happening.  For the Installer, you need to enter your password so the program can have elevated privileges to install programs like Python3 in the system area.  </li>
</ul>

Installation instructions:

1. Click [here to download the MacOSX patch file](https://github.com/WGSExtract/WGSExtract-Dev/blob/master/WGSExtract_MacOSX_Patch.zip). 
Your MacOSX will ask if it is OK to download from the github.com site.  Say OK.

2. Go to your Downloads directory and see the already unzipped archive folder there with 6 items inside (if not, click to unzip)

3. Drag those six items to your **WGSExtract** program top-level install directory.  There should be 3 **xxx_START.sh** files there already. For clarity, we assume below you have unpacked the **WGS Extract zip file** in your home directory of **~/WGSExtract**. 

4. Depending on the unzip program used and method of copy, the executable permission may have been stripped from the patch files and stept 5 won't work.  If so, via a Terminal command line, execute the following commands:  
   **chmod ugo+x Install_MacOSX.app/Contents/MacOS/applet**  
   **chmod ugo+x Start_MacOSX.app/Contents/MacOS/applet**

5. Double click on **Install_MacOSX.app** to run the installer (this was formerly the **MacOSX_START.sh** script). If you prefer, you can run the Installer from the Terminal command line via the command: **cd ~/WGSExtract; /bin/sh Install_MacOSX.sh**

6. Double click on **Start_MacOSX.app** to run the **WGS Extract** program itself (formerly the end of **MacOSX_START.sh** also).  If you prefer, you can run the program from the Terminal command line via the command: **cd ~/WGSExtract; /bin/sh Start_MacOSX.sh**
(the startscreen is quite small!)

7. You can create an alias of the **Start_MacOSX.app** file (right click, "Make Alias"), rename it (say to **WGSExtract**), 
and then move it to wherever you want to have an icon available to simply click and start the program.  Often the Applications
folder in Finder or maybe the ~/Desktop.

Why this patch: Since the initial MacOS release back in December, 2019, the **MacOS_start.sh** script has been broken. 
While we documented the work-around in the Users Manual, it has been a silent show stopper for many. Especially if they never see the manual.
This patch release finally resolves this problem more automatically until the next release which will include the fix.