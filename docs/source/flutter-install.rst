Flutter Install
===============

Create new app
--------------

The below command creates a Flutter project directory called myapp that contains a simple demo app that uses Material Components::

    macci:flutter cat$ flutter create smoketest_app
    Creating project smoketest_app...
    ...
    smoketest_app/test/widget_test.dart (created)
    Wrote 65 files.

    Running "flutter packages get" in smoketest_app...          10.2s

    [✓] Flutter is fully installed. (Channel beta, v0.2.3, on Mac OS X 10.13.3 17D47, locale en-US)
    [✓] Android toolchain - develop for Android devices is fully installed. (Android SDK 27.0.3)
    [✓] iOS toolchain - develop for iOS devices is fully installed. (Xcode 9.2)
    [✓] Android Studio is fully installed. (version 3.1)
    [✓] VS Code is fully installed. (version 1.21.1)
    [✓] Connected devices is fully installed. (1 available)

    All done! In order to run your application, type:

    $ cd smoketest_app
    $ flutter run

    Your main program file is lib/main.dart in the smoketest_app directory.

    macci:flutter cat$ cd smoketest_app/
    macci:smoketest_app cat$ flutter run
    Launching lib/main.dart on PH 1 in debug mode...
    Initializing gradle...                                      40.3s
    Resolving dependencies...                                   87.0s
    Running 'gradlew assembleDebug'...                          36.1s
    Built build/app/outputs/apk/debug/app-debug.apk (25.6MB).
    Installing build/app/outputs/apk/app.apk...                  8.4s
    I/FlutterActivityDelegate(18711): onResume setting current activity to this
    Syncing files to device PH 1...                              2.3s

    🔥  To hot reload your app on the fly, press "r". To restart the app entirely, press "R".
    An Observatory debugger and profiler on PH 1 is available at: http://127.0.0.1:8100/
    For a more detailed help message, press "h". To quit, press "q".
    D/EssentialLetterbox(18711): setting letterbox insets Handler (android.view.ViewRootImpl$ViewRootHandler) {b3e007f}


In the project directory, the code for your app is in lib/main.dart.

Run the app
-----------

 #. Make sure a target device is selected in the lower, right-hand corner of VS Code
 #. Press the F5 button on the keyboard, or invoke Debug>Start Debugging
 #. Wait for the app to launch

If everything works, after the app has been built, you should see your starter app on your device.

Mod the app
-----------

Edit lib/main.dart change "Flutter Demo Home Page" to "Flutter Smoke Test".  Go to terminal and press "r" to reload.  The smoketest_app should update.

=============
Check Flutter
=============

Should run the following and get the same results::

    macci:~ cat$ flutter doctor
    Doctor summary (to see all details, run flutter doctor -v):
    [✓] Flutter (Channel beta, v0.2.3, on Mac OS X 10.13.3 17D47, locale en-US)
    [✓] Android toolchain - develop for Android devices (Android SDK 27.0.3)
    [✓] iOS toolchain - develop for iOS devices (Xcode 9.2)
    [✓] Android Studio (version 3.1)
    [✓] VS Code (version 1.21.1)
    [✓] Connected devices (1 available)

    • No issues found!
    macci:~ cat$ 

===============
Get Flutter SDK
===============

To get Flutter, use git to clone the repository and then add the flutter tool to your path. Running flutter doctor shows any remaining dependencies you may need to install::

    macci:Code cat$ pwd
    /Users/cat/Code
    macci:Code cat$ git clone -b beta https://github.com/flutter/flutter.git
    Cloning into 'flutter'...
    remote: Counting objects: 117816, done.
    remote: Compressing objects: 100% (53/53), done.
    remote: Total 117816 (delta 20), reused 21 (delta 11), pack-reused 117752
    Receiving objects: 100% (117816/117816), 35.29 MiB | 3.29 MiB/s, done.
    Resolving deltas: 100% (88269/88269), done.
    macci:Code cat$ export PATH=`pwd`/flutter/bin:$PATH
    macci:Code cat$ flutter doctor
    Downloading Dart SDK from Flutter engine e61bb9ac3a3fd789754e2e54220bcfc27076a857...
    % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                    Dload  Upload   Total   Spent    Left  Speed
    100 44.3M  100 44.3M    0     0  3218k      0  0:00:14  0:00:14 --:--:-- 3264k
    Building flutter tool...

    ╔════════════════════════════════════════════════════════════════════════════╗
    ║                 Welcome to Flutter! - https://flutter.io                   ║
    ║                                                                            ║
    ║ The Flutter tool anonymously reports feature usage statistics and crash    ║
    ║ reports to Google in order to help Google contribute improvements to       ║
    ║ Flutter over time.                                                         ║
    ║                                                                            ║
    ║ Read about data we send with crash reports:                                ║
    ║ https://github.com/flutter/flutter/wiki/Flutter-CLI-crash-reporting        ║
    ║                                                                            ║
    ║ See Google's privacy policy:                                               ║
    ║ https://www.google.com/intl/en/policies/privacy/                           ║
    ║                                                                            ║
    ║ Use "flutter config --no-analytics" to disable analytics and crash         ║
    ║ reporting.                                                                 ║
    ╚════════════════════════════════════════════════════════════════════════════╝
    
    Downloading Material fonts...                                0.8s
    Downloading package sky_engine...                            0.5s
    Downloading common tools...                                  1.9s
    Downloading darwin-x64 tools...                              8.6s
    Downloading android-arm-profile/darwin-x64 tools...          1.3s
    Downloading android-arm-release/darwin-x64 tools...          1.1s
    Downloading android-arm64-profile/darwin-x64 tools...        1.3s
    Downloading android-arm64-release/darwin-x64 tools...        1.2s
    Downloading android-x86 tools...                             5.1s
    Downloading android-x64 tools...                             5.4s
    Downloading android-arm tools...                             2.7s
    Downloading android-arm-profile tools...                     2.3s
    Downloading android-arm-release tools...                     2.0s
    Downloading android-arm64 tools...                           2.9s
    Downloading android-arm64-profile tools...                   2.4s
    Downloading android-arm64-release tools...                   2.2s
    Downloading ios tools...                                     7.1s
    Downloading ios-profile tools...                             6.7s
    Downloading ios-release tools...                             6.3s
    Downloading Gradle Wrapper...                                0.2s
    Doctor summary (to see all details, run flutter doctor -v):
    [✓] Flutter (Channel beta, v0.2.3, on Mac OS X 10.13.3 17D47, locale en-US)
    [✗] Android toolchain - develop for Android devices
        ✗ Unable to locate Android SDK.
        Install Android Studio from: https://developer.android.com/studio/index.html
        On first launch it will assist you in installing the Android SDK components.
        (or visit https://flutter.io/setup/#android-setup for detailed instructions).
        If Android SDK has been installed to a custom location, set $ANDROID_HOME to that location.
    [!] iOS toolchain - develop for iOS devices
        ✗ Xcode installation is incomplete; a full installation is necessary for iOS development.
        Download at: https://developer.apple.com/xcode/download/
        Or install Xcode via the App Store.
        Once installed, run:
            sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
        ✗ Brew not installed; use this to install tools for iOS device development.
        Download brew at https://brew.sh/.
    [✗] Android Studio (not installed)
    [!] VS Code (version 1.21.1)

    ! Doctor found issues in 4 categories.
    macci:Code cat$ 

=====================
iOS toolchain Install
=====================

Flutter uses the iOS toolchain to produce iOS Applications.

 #. Launch App Store, search for xcode, click install, enter apple ID.
    #. After xcode install run::

        macci:Code cat$ sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer

 #. Accept xcode lic by running the following::

        macci:Code cat$ sudo xcodebuild -license

 #. Enable developer mode::

        macci:Code cat$ sudo DevToolsSecurity -enable
    
 #. Brew-Install_ download at https://brew.sh/ or the following::

        macci:Code cat$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

 #. Install brew libs
    #. brew install --HEAD libimobiledevice
    #. brew install ideviceinstaller
    #. brew install ios-deploy
    #. brew install cocoapods
    #. pod setup

=========================
Andriod toolchain Install
=========================

Flutter uses the Android toolchain to produce Android Applications.

 #. Install Android-Studio_ from https://developer.android.com/studio/index.html
 #. Launch android-studio-ide-173.4670197-mac.dmg
 #. Drag and Drop Icon into Applications
 #. Launch Android Studio App
 #. Follow setup (I did not import anything)
 #. Need to allow "App Store and identified developers" in Security System Preferences.
 #. Accept Lic run::

        macci:Code cat$ flutter doctor --android-licenses

====================
Andriod Device Setup
====================

We need and Android device and simulator setup.

 #. Enable Developer options and USB debugging via Android-Device-DevOptions_
    #. On device, open "Settings"
    #. Select System -> About phone -> tap Build number 7 times.
    #. Enter PIN and it should tell you "Your a Developer now."
    #. Go to System -> Developer
    #. Enable "USB debugging"

==============
vscode Install
==============

I like vscode... so I use it vscode-install_ 

 #. Download vscode for mac vscode-mac-Install_
 #. Drag vscode app to Applications Directory
 #. Add vscode to Dock
 #. Add vscode to path (manually)::

     cat << EOF >> ~/.bash_profile
     # Add Visual Studio Code (code)
     export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
     EOF

==========
References
==========

 + Created via Flutter-Mac-Install_
 + Brew-Install_
 + Android-Studio_
 + Android-Device-DevOptions_

.. _Flutter-Mac-Install: https://flutter.io/setup-macos/
.. _Brew-Install: https://brew.sh/
.. _Android-Studio: https://developer.android.com/studio/index.html
.. _Android-Device-DevOptions: https://developer.android.com/studio/debug/dev-options.html
.. _vscode-install: https://code.visualstudio.com/docs/setup/setup-overview
.. _vscode-mac-install: https://code.visualstudio.com/docs/setup/mac


