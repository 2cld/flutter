Flutter dev smoke
=================

==============
Smoke Test App
==============

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


Smoke Test App augmentation
===========================

Guide
^^^^^

.. toctree::
   :maxdepth: 2

   flutter-dev-smoke-chat
   flutter-dev-smoke-maps
   flutter-dev-smoke-qr


