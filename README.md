# TWA Browser Support Test
## Table of Contents
- [Introduction](#introduction)
- [Demo](#demo)
- [Results](#results)
- [Setup](#setup)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Introduction
The purpose of this Android project is to demonstrate how to test whether a specific browser supports [Trusted Web Activities (Android Browser Helper)](https://github.com/GoogleChrome/android-browser-helper). 

## Demo
For a quick and simple test, the `TwaBrowserSupportTest.apk` has been included in the root directory of this project.

## Results
Based on the test results, it appears that most modern browsers support TWA and are able to hide the navigation bar when the assetlinks.json is properly configured on the website and the SHA256 matches on the keystore.

It's interesting to note that:
- The three browsers at the bottom of the table were unable to open from the TwaLauncher. 
- Out of the browsers that were able to launch from the TwaLauncher, the Huawei Browser was the only browser that did not support TWA as it did not hide the navigation bar.

| **Browser** | **Package Name** | **Could launch w/ TwaLauncher?** | **Twa Support** |
|--|--|:--:|:--:|
| Chrome | com.android.chrome | :white_check_mark: | :white_check_mark: |
| Firefox | org.mozilla.firefox | :white_check_mark: | :white_check_mark: |
| Edge | com.microsoft.emmx | :white_check_mark: | :white_check_mark: |
| Huawei Browser | com.huawei.browser | :white_check_mark: | :x: |
| Samsung Internet | com.sec.android.app.sbrowser | :white_check_mark: | :white_check_mark: |
| Brave Browser | com.brave.browser | :white_check_mark: | :white_check_mark: |
| Opera | com.opera.browser | :x: | :x: |
| DuckDuckGo Browser | com.duckduckgo.mobile.android | :x: | :x: |
| UC Browser | com.UCMobile.intl | :x: | :x: |

## Setup

### Add a New Browser
If you want to test for additional browsers, you will need to make two changes. 
1. Add a new function similar to [`launchChrome()`](https://github.com/bryantvu/TWA-Browser-Support-Test/blob/377a96f5d15ca453cc4deed923dad289aa219273/app/src/main/java/com/pictroom/android/LaunchTwaActivity.java#L155) in [`LaunchTwaActivity.java`](https://github.com/bryantvu/TWA-Browser-Support-Test/blob/master/app/src/main/java/com/pictroom/android/LaunchTwaActivity.java) and change the parameter of the inner function `initLaunch` to the package name of the target browser.
2. Add a new button in [`activity_launch_twa.xml`](https://github.com/bryantvu/TWA-Browser-Support-Test/blob/master/app/src/main/res/layout/activity_launch_twa.xml) similar to the one for [`Launch Chrome`](https://github.com/bryantvu/TWA-Browser-Support-Test/blob/377a96f5d15ca453cc4deed923dad289aa219273/app/src/main/res/layout/activity_launch_twa.xml#L60) and point it to your function in `LaunchTwaActivity.java`.

### Change Host URL
Changing the [current target website](https://pictroom.com) is **NOT** recommended, as it can be a complicated process. In order for the navigation bar to hide when loading a website, the [assetlinks.json](https://developers.google.com/digital-asset-links/v1/getting-started) has to be configured and the SHA256 of the keystore must match. Configuring the assetlinks.json requires developer access to the target website.

## License

This Android sample code is licensed under the  [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0)

## Acknowledgements
The code in this project has been modified from the [twa-custom-launcher](https://github.com/GoogleChrome/android-browser-helper/tree/main/demos/twa-custom-launcher) demo found inside of [Android Browser Helper](https://github.com/GoogleChrome/android-browser-helper)
