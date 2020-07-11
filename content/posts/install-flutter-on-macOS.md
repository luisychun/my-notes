---
title: "Install Flutter on macOS"
date: 2020-07-05T18:28:23+08:00
tags: []
draft: false
---

### Install Flutter on masOS

### Download Flutter SDK and setup path

- Navigate to Flutter official [doc](https://flutter.dev/docs/get-started/install/macos) to download and install the Flutter sdk
- Update the PATH variable permanently, check which shell you are using with **echo $SHELL**
- If you are using BASH, edit **$HOME/.bash_profile**, if you are using Z shell, edit **$HOME/.zshrc**
- Add the following line **export PATH = $PATH:[PATH_TO_FLUTTER_SDK_DIRECTORY]/flutter/bin**
- Replace **[PATH_TO_FLUTTER_SDK_DIRECTORY]** to be the path where you installed the flutter sdk
- Close the current terminal window and open a new one, **echo $PATH** to verify that the flutter/bin directory is now in your PATH
- To check if there are any dependencies you need to install to complete the setup, **flutter doctor**

### Environment/Platform setup

**iOS**
- Download [Xcode](https://apps.apple.com/us/app/xcode/id497799835)
- Configure the Xcode command-line-tools with following
- **sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer**
- **sudo xcodebuild -runFirstLaunch**
- Make sure the Xcode licenses agreements is signed **sudo xcodebuild -license**
- Then you can setup the iOS simulator with **open -a Simulator**

**Android**
- Download and install [Android Studio](https://developer.android.com/studio)
- Open the Android Studio, and open existing flutter project that we created above
- Make sure the Android Virtual Device is installed
- Install the flutter and dart plugin that provided by IDE
- If facing any SDK licenses are not accepted, **flutter doctor --android-licenses**

### Create and run a simple Flutter app

```shell
flutter create my_app
cd my_app
flutter run
```

**Before running the Flutter app, make sure the simulator is already up**

**iOS**
- Open terminal and type **open -a Simulator**

**Android**
- Open Android Studio
- Navigate to top menu bar, select Tools > AVD Manager
- Select a virtual device and click the **Play** button as diagram below

{{< rawhtml >}}
  <img class="ui fluid image" src="/img/AVD.png">
{{< /rawhtml >}}