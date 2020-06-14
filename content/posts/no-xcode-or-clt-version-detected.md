---
title: "macOS Catalina gyp: No Xcode or CLT Version Detected"
date: 2020-06-14T17:23:22+08:00
tags: []
draft: false
---

## Error appear every time when running `npm install` or `yarn install`
[gyp: No Xcode or CLT version detected macOS Catalina | Anansewaa](https://medium.com/flawless-app-stories/gyp-no-xcode-or-clt-version-detected-macos-catalina-anansewaa-38b536389e8d)

Reinstall command-line-tools do resolve the issue.

First, open terminal and type `xcode-select --print-path` to get installed command line tool path. Then remove it with `sudo` privilege `sudo rm -r -f <path>`. Install back with `xcode-select --install`, agree to the license to proceed with the installation.