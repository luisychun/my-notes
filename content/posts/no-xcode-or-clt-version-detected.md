---
title: "macOS Catalina gyp: No Xcode or CLT Version Detected"
date: 2020-06-14T17:23:22+08:00
tags: ["Issue"]
draft: false
---

### Reference
[gyp: No Xcode or CLT version detected macOS Catalina | Anansewaa](https://medium.com/flawless-app-stories/gyp-no-xcode-or-clt-version-detected-macos-catalina-anansewaa-38b536389e8d)

### Error appear when running `npm install` or `yarn install`

Reinstall command-line-tools do resolve the issue

First, open terminal and type **xcode-select --print-path** to get installed command line tool path. Then remove it with **sudo** privilege **sudo rm -r -f <path>**. Reinstall with **xcode-select --install**, and proceed with the installation