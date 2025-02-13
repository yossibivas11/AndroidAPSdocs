# Building the APK

## Build yourself instead of download

**AndroidAPS is not available as download due to regulation for medial devices. It is legal to build the app for your own use but you must not give a copy to others! See [FAQ page](../Getting-Started/FAQ.md) for details.**

## Important notes

* Please use **[Android Studio Version 4.1.1](https://developer.android.com/studio/)** or newer to build the apk.
* [Windows 10 32-bit systems](../Installing-AndroidAPS/troubleshooting_androidstudio#unable-to-start-daemon-process) are not supported by Android Studio 4.1.1.

**Configuration on demand** is not supported by the current version of the Android Gradle plugin! 

If your build fails with an error regarding "on demand configuration" you can do the following:
* Open the Preferences window by clicking File > Settings (on Mac, Android Studio > Preferences).
* In the left pane, click Build, Execution, Deployment > Compiler.
* Uncheck the Configure on demand checkbox.
* Click Apply or OK.

## Recommended specification of computer for building apk file

<table class="tg">
<thead>
  <tr>
    <th class="tg-baqh">OS(Only 64 bit)</th>
    <th class="tg-baqh">Windows 8 or higher</th>
    <th class="tg-baqh">Mac OS 10.14 or higher</th>
    <th class="tg-baqh">Any Linux supports Gnome, KDE, or Unity DE;&nbsp;&nbsp;GNU C Library 2.31 or later</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-baqh"><p align="center">CPU(Only 64 bit)</td>
    <td class="tg-baqh">x86_64 CPU architecture; 2nd generation Intel Core or newer, or AMD CPU with support for a <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-windows" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Windows Hypervisor</span></a></td>
    <td class="tg-baqh">ARM-based chips, or 2nd generation Intel Core or newer with support for <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-mac" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Hypervisor.Framework</span></a></td>
    <td class="tg-baqh">x86_64 CPU architecture; 2nd generation Intel Core or newer, or AMD processor with support for AMD Virtualization (AMD-V) and SSSE3</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">RAM</td>
    <td class="tg-baqh" colspan="3"><p align="center">8GB or more</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Disk</td>
    <td class="tg-baqh" colspan="3"><p align="center">At least 30GB free space. SSD is recommended.</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Resolution</td>
    <td class="tg-baqh" colspan="3"><p align="center">1280 x 800 Minimum <br></td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Internet</td>
    <td class="tg-baqh" colspan="3"><p align="center">Broadband</td>
  </tr>
</tbody>
</table>

Please be in mind that both **64 bit CPU and 64 bit OS are mandatory condition.** If your system DOES NOT meet this condition, you have to change affected hardware or software or the whole system. **It is strongly recommended to use SSD(Solid State Disk) instead of HDD(Hard Disk Drive) because it will take less time when you are building the APS installation apk file.** Recommended is just recommended and it is not a mandatory. However, you may still use a HDD when you are building apk file if you can spend a long time ALONE to complete the build.
   
---
### This article is divided into two parts.
* In the overview part there is an explanation on what steps are necessary to build the APK file.
* In the step by step walkthrough part you will find the screenshots of a concrete installation. Because the versions of Android Studio - the software development environment which we will use to build the APK - will change very quickly this will be not identical to your installation but it should give you a good starting point. Android Studio also runs on Windows, Mac OS X and Linux and there might be small differences in some aspects between each platform. If you find that something important is wrong or missing, please inform the facebook group "AndroidAPS users" or in the Discord chat [Android APS](https://discord.gg/4fQUWHZ4Mw) so that we can have a look at this.

## Overview

In general, the steps necessary to build the APK file:

1. [Install git](../Installing-AndroidAPS/git-install.rst)
2. [Install Android Studio](../Installing-AndroidAPS/Building-APK#install-android-studio)
3. [Set git path in Android Studio preferences](../Installing-AndroidAPS/Building-APK#set-git-path-in-preferences)
4. [Download AndroidAPS code](../Installing-AndroidAPS/Building-APK#download-androidaps-code)
5. [Download Android SDK](../Installing-AndroidAPS/Building-APK#download-android-sdk)
6. [Build the app](../Installing-AndroidAPS/Building-APK#generate-signed-apk) (generate signed apk)
7. [Transfer apk file to your phone](../Installing-AndroidAPS/Building-APK#transfer-apk-to-smartphone)
8. [Identify receiver if using xDrip+](../Installing-AndroidAPS/Building-APK#identify-receiver-if-using-xdrip)


## Step by step walkthrough

Detailed description of the steps necessary to build the APK file.

## Install git (if you don't have it)

Follow the manual on the [git installation page](../Installing-AndroidAPS/git-install.rst).

## Install Android Studio

The following screenshots have been taken from Android Studio Version 3.6.1. Your screen might look a bit different if you use a newer version of Android Studio. But you should be able to find your way through. [Help from the community](../Where-To-Go-For-Help/Connect-with-other-users.md) is provided.

One of the most important things when installing Android Studio: **Be patient!** During installation and setup Android Studio is downloading a lot of stuff which will take its time.

Install [Android Studio](https://developer.android.com/studio/install.html) and setup during first start.

Select "Do not import settings" as you have not used it before.

   ![Do not import settings](../images/AndroidStudio361_01.png)

Decide whether you want to share data with Google or not.

   ![Share data with Google](../images/AndroidStudio361_02.png)

On the following screen click "Next".

   ![Welcome screen](../images/AndroidStudio361_03.png)

Select "Standard" installation and click "Next".

   ![Standard installation](../images/AndroidStudio361_04.png)

Select the theme for the user interface you like. (In this manual we used "Light".) Then click "Next".
This is just the color scheme. You can select any you like (i.e. "Darcula" for dark mode). This selection has no influence on building the APK.

   ![UI color scheme](../images/AndroidStudio361_05.png)

Click "Finish" on the "Verify Settings" dialog.

   ![Verify settings](../images/AndroidStudio361_06.png)

Wait while Android Studio downloads additional components and be patient. Once everything is downloaded button "Finish" turns blue. Click the button now.

   ![Downloading components](../images/AndroidStudio361_07.png)


## Set git path in preferences

Make sure [git is installed](../Installing-AndroidAPS/git-install.rst) on your computer.

On the Android Studio welcome screen click the small triangle (1. in next screenshot) and select "Settings" (2.).

   ![Android Studio settings from welcome screen](../images/AndroidStudio361_08.png)


### Windows

* Click the small triangle next to Version Control (1.) to open the sub-menu.
* Click Git (2.).
* Make sure update method "Merge" (3.) is selected.
* Check if Android Studio can locate path to git.exe automatically by clicking the button "Test" (4.)

   ![Android Studio settings](../images/AndroidStudio361_09.png)

* If automatic setting is successful git version will be displayed.
* Click "OK" in the dialog box (1.) and "OK" in the settings window (2.).

   ![Automatic git installation succeeded](../images/AndroidStudio361_10.png)

* In case file git.exe cannot be found click "OK" in the dialog box (1.) and then the button with the three dots (2.).
* Use [search function](https://www.tenforums.com/tutorials/94452-search-file-explorer-windows-10-a.html) in windows explorer to find "git.exe" if you are unsure where it can be found. You are looking for git.exe located in \bin\ folder.
* Select path to git.exe and make sure you selected the one in ** \bin\ ** folder (3.) and click "OK" (4.).
* Close settings window by clicking "OK" button (5.).

   ![Automatic git installation failed](../images/AndroidStudio361_11.png)

* **Reboot your computer to update system environment.**

### Mac

* Any git version should work. For example [https://git-scm.com/download/mac](https://git-scm.com/download/mac).
* Use homebrew to install git: ```$ brew install git```.
* For details on installing git see the [official git documentation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* If you install git via homebrew there is no need to change any preferences. Just in case: They can be found here: Android Studio - Preferences.


## Download AndroidAPS code

* **If you haven't already rebooted your computer after setting git path in preferences do it now. System environment must be updated.**

* There are two options to start a new project:

   * On the Android Studio welcome screen click "Get from version control"

      ![Check out project from version control from welcome screen](../images/AndroidStudio_GetFromVersionControl.PNG)

   * If you already opened Android Studio and do not see the welcome screen anymore select File (1.) > New (2.) > Project from Version Control... (3.)

      ![Check out project from version control within Android Studio](../images/AndroidStudio_FileNew.PNG)

* Fill in the URL to the main AndroidAPS repository (https://github.com/nightscout/AndroidAPS) (1.).
* Choose the directory where you want to save the cloned code. (2.)
* Click button "Clone" (3.).

   ![Clone repository](../images/AndroidStudio_NewURL.PNG)

* Do not click "Background" while repository is cloned!

   ![No background action](../images/AndroidStudio361_15.png)

* After repository is cloned successfully open your local copy by clicking "Yes".

   ![Open repository](../images/AndroidStudio361_16.png)

* In the lower right corner you will see the information that Android Studio is running background tasks.

   ![Background tasks](../images/AndroidStudio361_17.png)

* Grant access if your firewall is asking for permission.

   ![Firewall permission java](../images/AndroidStudio361_18.png)

* Once the background tasks are finished you will probably see the following error message: 

   ![SDK licence](../images/AndroidStudio361_19.png)

## Download Android SDK

* Click File > Settings.

   ![Open settings](../images/AndroidStudio361_20.png)

* Click the small triangle next to Appearance & Behaviour (1.).
* Click the small triangle next to System Settings (2.) and select Android SDK (3.)
* Check the box left of "Android 9.0 (Pie)" (4.) (API Level 28).

   ![SDK settings](../images/AndroidStudio361_21.png)

* Confirm changes by clicking OK.

   ![Confirm SDK changes](../images/AndroidStudio361_22.png)

* Accept licence agreement (1.) and click "Next" (2.).

   ![Accept SDK licence](../images/AndroidStudio361_23.png)

* Wait until installation is finished.

   ![Wait during SDK installation](../images/AndroidStudio361_24.png)

* When SDK installation is completed the "Finish" button will turn blue. Click this button.

   ![Finish SDK installation](../images/AndroidStudio361_25.png)

* Android Studio might recommend to update the gradle system. **Never update gradle!** This might lead to difficulties!
* If you see an information on the lower right side of your Android Studio window that Android Gradle Plugin is ready to update click on the text "update" (1.) and in the dialog box on "Don't remind me again for this project" (2.).

   ![No cradle update](../images/AndroidStudio361_26.png)


## Generate signed APK

Signing means that you indicate your app to be your own creation but in a digital way as a kind of digital fingerprint within the app itself. That is necessary because Android has a rule that it only accepts signed code to run for security reasons. For more information on this topic, follow [this link](https://developer.android.com/studio/publish/app-signing.html#generate-key).

* Click "Build" in the menu bar and select "Generate Signed Bundle / APK...".

   ![Build apk](../images/AndroidStudio361_27.png)

* Select "APK" (1.) instead of "Android App Bundle" and click "Next" (2.).

   ![APK instead of bundle](../images/AndroidStudio361_28.png)

* Make sure that module is set to "app" (1.).
* Click "Create new..." (2.) to start creating your key store. 

   A key store in this case is nothing more than a file in which the information for signing is stored. It is encrypted and the information is secured with passwords. 

   ![Create key store](../images/AndroidStudio361_29.png)

* Click the folder symbol (1.) to select your key store path. 
* Select the path where your key store shall be saved (2.). **Do not save in same folder as project. You must use a different directory!** One option might be your home folder.
* Type a file name for your key store (3.).
* Click "OK" (4.).
* Passwords for key store and key do not have to be very sophisticated. Make sure to remember those or make a note in a safe place. In case you will not remember your passwords in the future you see [troubleshooting for lost key store](../Installing-AndroidAPS/troubleshooting_androidstudio#lost-keystore).
* Enter (5.) and confirm (6.) the password for your key store.
* Do the same for your key (7. + 8.).
* Validity (9.) is 25 years by default. You do not have to change the default value.
* First and last name must be entered (10.). All other information is optional.
* Click "OK" (11.) when you are done.

   ![Key store path](../images/AndroidStudio361_30.png)

* Make sure the box to remember passwords is checked (1.). So you don't have to enter them again next time you build the apk (i.e. when updating to a new AndroidAPS version).
* Click "Next" (2.).

   ![Remember passwords](../images/AndroidStudio361_31.png)

* Select build variant "fullRelease" (1.). 
* Check boxes V1 and V2 for signature versions (2.).
* Click "Finish". (3.)

   ![Finish build](../images/AndroidStudio361_32.png)

* Android Studio will display the information "APK(s) generated successfully..." after build is finished.
* In case build was not successful refer to the [troubleshooting section](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).
* Easiest way to find the apk is to click on "Event log".

   ![Build successfully - event log](../images/AndroidStudio361_33.png)

* In the event log section click "locate".

   ![Event log - locate apk](../images/AndroidStudio361_34.png)

* app-full-release.apk is the file you are looking for.

   ![File location apk](../images/AndroidStudio361_35.png)


## Transfer APK to smartphone

Easiest way to transfer app-full-release.apk to your phone is via [USB cable or Google Drive](https://support.google.com/android/answer/9064445?hl=en). Please note that transfer by mail might cause difficulties and is not the preferred way.

On your phone you have to allow installation from unknown sources. Manuals how to do this can be found on the internet (i.e. [here](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) or [here](https://www.androidcentral.com/unknown-sources)).


## Identify receiver if using xDrip+

[See xDrip+ page](../Configuration/xdrip#identify-receiver)


## Troubleshooting

See separate page [troubleshooting Android Studio](../Installing-AndroidAPS/troubleshooting_androidstudio.rst).
