# my_ios_app

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

This project is a starting point for a Flutter application.
A few resources to get you started if this is your first Flutter project:

Lab: Write your first Flutter app
Cookbook: Useful Flutter samples
For help getting started with Flutter development, view the online documentation, which offers tutorials, samples, guidance on mobile development, and a full API reference.

Setup editor for flutter for ios
This document was created for the purpose of setting up an appropriate IDE or SDK for running successfully the livil workspace for development to deployment of the company's ios product app.

Consideration : This setup is done on Mac OS (Apple Chip M1) and valid for mac users. For windows user follow this (https://docs.flutter.dev/get-started/install/windows)

System Requirements
Recommended latest version of all the below mentioned softwares

Operating System : Ventura 13.2
Required Softwares
[Android SDK - Electric Eel](https://developer.android.com/studio)
[Visual Studio Code](https://code.visualstudio.com/)
[Xcode] (https://developer.apple.com/xcode/)
[Flutter SDK](https://docs.flutter.dev/get-started/install/macos)
Steps to follow
Download the following installation bundle to get the latest stable release of the flutter SDK : **flutter_macos_arm64_3.7.1-stable.zip** (Make sure to check your system configuration before installation, in case you have different configuration then download another flutter sdk ) (https://docs.flutter.dev/get-started/install/macos)

Extract the file in the desired folder location, for example:
`cd ~/development`
`unzip ~/Downloads/flutter_macos_3.7.1-stable.zip`
OR
You can either download the SDK, from your favorite terminal, navigate into the folder where you want to download the SDK, and clone the SDK into the folder.

`cd development` `git clone https://github.com/flutter/flutter.git -b stable`
Add Flutter to your Path - To run **flutter** commands in any terminal session, we have to add the Flutter SDK to our system's PATH variable.

First, we will find the path to our Flutter bin folder. The easiest way to do this is by using the terminal to navigate into the flutter/bin folder and use the pwd command to print the current working directory.

    `cd development/flutter/bin`

    `pwd`

    you will see result like this:
    /Users/@foobar/development/flutter/bin

    Copy the path showing in the above result.

Add this path to your ** ~/.zshrc ** , open the file with nano editor in terminal. To open this file, type this command: `nano ~/.zshrc`
Add a new line to export the path to your Flutter bin directory.
export PATH=”$PATH:[PATH_OF_FLUTTER_BIN_DIRECTORY]”
For saving this, hit control + x to save your changes and close.
Terminal will not pick up the altered PATH automatically. For our change to have effect, we need to either restart the terminal or source the file.

`source ~/.zshrc`
We can now verify that the flutter command can be found.
`which flutter`
result:
/User/@foobar/tools/flutter/bin/flutter
Now that we can run flutter commands, we can have access to Flutter doctor. The flutter doctor command displays the status of your Flutter installation and tells you what dependencies are missing.

`flutter doctor`
The results of flutter doctor, the First time I ran the command, with few red checkmarks.

Check response here(/assets//Users/manishparihar/Desktop/flutter-doctor-initialresponse.png "flutter doctor")
Basically, Flutter doctor tells us that we have an incomplete Xcode installation and no Android toolchain. So, we can fix it now.

Xcode and CocoaPods - Since, we are not sure which part of our Xcode is missing, so we will install the complete xcode via the **Mac App Store**. Once you installed the Xcode, run the commands suggested by Flutter doctor.

        `sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer`

        `sudo xcodebuild -runFirstLaunch`

Next, Flutter says you don't have cocoapod installed , so run this command as well on the terminal.

    `sudo gem install cocoapods`

    <p> Then run **flutter doctor** command on the terminal, it will give you a **green checkmark** on your Xcode part.

        For IOS Simulator you don't have to do any settings.
    </p>

Android toolchain - For building an ios app you don't need an android tool chain, but in future, if you want to build an android app then setup the Android toolchain as well.

Download and install Android Studio (from above mentioned link).
Now run flutter doctor and see if everything works, in case you see a weird problem that is not mentioned in Flutter’s documentation. Flutter doctor said it was **“Unable to find bundled Java version”** for Android Studio.

We need to set **JAVA_HOME** environment variable. First we need to download the JDK. **Select Arm 64 DMG Installer** - (For Apple Mac M1 user ) Extract the dmg file here

Open your terminal and run command **java –version** Once you see current version of java shows in terminal

Go to menu **“Go to Folder”** option and Enter **“/Library/Java”** and when you see option like **/Library/Java/JavaVirtualMachines**

Select JavaVirtualMachine and **right click** -> **New Terminal at Folder**
Create the profile file: `vim ~ /.bash_profile`
Enter the Java Home path:
`export JAVA_HOME= /Library/Java/JavaVirtualMachines/jdk-19.2.jdk/Contents/Home`
Save the changes by running** “:wq!” ** and apply the changes.
Just to make sure everything went right run `source ~/.bash_profile`
Check the path with command : `echo $JAVA_HOME`
Accept the Android licenses - After fixing the “Unable to find bundled Java Version” problem, the only thing left to do is to accept the Android licenses and we are good to go. `flutter doctor --android-licenses` Run above command and accept all the licenses one by one

Finally, I ran the flutter doctor again to see the result with success.
Once all settings are done. You can open workspace and type command `flutter run`
Step for future integration:
Further process we can add once we set up the project. For running the code successfully.

Add appropriate workspace with required dependencies / plug-ins / framework installed in VS Code.
