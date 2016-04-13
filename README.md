## Crosswalk
[Crosswalk](http://crosswalk-project.org) is a web runtime for mobile and desktop
web applications.

## CSS Round Display
[CSS Round Display](https://drafts.csswg.org/css-round-display/) is CSS specifications
for round display, which allow the users to create content for the round display.
This git repository provides some sample web applications for Android Wear device,
which are packaged with Crosswalk web runtime.

For your information, CSS Round Display has been experimentally implemented in Crosswalk
for Android wear so the latest changes of the specification could not be applied to the implementation.


## Build Crosswalk for Android Wear
You can build Crosswalk for Android Wear including CSS Round Display features as follows:
* https://github.com/joone/wiki/wiki/Build-Crosswalk-for-Android-Wear
* https://crosswalk-project.org/contribute/building_crosswalk.html

```
$ ninja -C out/Release xwalk_app_template
```

You need to create VERSION file in crosswalk/src/out/Release/xwalk_app_template/,
which includes the following information:
```
MAJOR=16
MINOR=45
BUILD=421
PATCH=19
```

## Package round display applications with Crosswalk
You can easily package your Crosswalk application with [crosswalk app tools](https://github.com/crosswalk-project/crosswalk-app-tools)

1. Download corsswalk_app_tools and set it up for Android.
1. Download Crosswalk web runtime built with CSS Round Display implementation( [x86](https://github.com/joone/crosswalk-round-display-samples/raw/master/crosswalk/crosswalk-19.49.506.0.x86-round-display.tar.gz),[arm](https://github.com/joone/crosswalk-round-display-samples/blob/master/crosswalk/crosswalk-16.45.421.19-round-dsplay.tar.gz)). for Android Wear.

2. Extract it to $HOME/Downloads/.
3. Clone this repository and change to the directory:
`` cd ~/git/crosswalk-round-display-samples`` 

4. Choose a sample directory and run crosswalk-pkg tools:
```
$ crosswalk-pkg -p android -c ~/Download/xwalk_app_template polar
$ adb install -r com.joone.polar-0.1-debug.x86.apk
```
For [shared mode](https://crosswalk-project.org/documentation/shared_mode.html), you can only package HTML,CSS, JS and other resource files without Crosswalk engine. In this case, Crosswalk engine is shared with other Crosswalk Web applications on Android.
```
$ crosswalk-pkg  -p android -a shared  -c ~/git/crosswalk/src/out/Release/xwalk_app_template weather
```
You can download Crosswalk engine for shared mode at the links below:
* [x86](https://github.com/joone/crosswalk-round-display-samples/raw/master/crosswalk/XWalkRuntimeLibX86.apk)
* [arm](https://github.com/joone/crosswalk-round-display-samples/raw/master/crosswalk/XWalkRuntimeLib.apk)

## Download sample applications built with Crosswalk for Android Wear
You can download Crosswalk sample applications for Android Wear at [here](https://github.com/joone/crosswalk-round-display-samples/tree/master/apk).

## Reference
* https://github.com/anawhj/jRound

## Tips
### List up applicaitons in Android
```
$ adb shell 'pm list package -f' 
$ adb shell pm uninstall -k com.joone.rd
```

### Setup Android SDK
Edit ~/.bashrc file and add the Android SDK tools path.
```
vi ~/.bashrc
```
Add the following lines in it. Make sure you’ve added the correct path of android tools path as shown below.
```
export ANDROID_HOME=/home/joone/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
```
Save and close the file.
