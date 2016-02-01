# crosswalk-round-display-samples
Sample Web applications of Crosswalk web runtime for CSS Round Display


# Package your Crosswalk application

You can package your Crosswalk application with crosswalk app tools:
https://github.com/crosswalk-project/crosswalk-app-tools

Download https://github.com/joone/crosswalk-round-display-samples/blob/master/crosswalk/crosswalk-16.45.421.19-round-dsplay.tar.gz.
Extract it to ~/Download/.


```
$ crosswalk-pkg  -p android -c ~/Download/crosswalk-16.45.421.19-round-display polar
$ adb install -r com.joone.polar-0.1-debug.armeabi-v7a.apk

```


# Build Crosswalk for Android
* https://github.com/joone/wiki/wiki/Build-Crosswalk-for-Android-Wear
* https://crosswalk-project.org/contribute/building_crosswalk.html

``
$ ninja -C out/Release xwalk_app_template
``

You need to create VERSION file in crosswalk/src/out/Release/xwalk_app_template/, which includes
the folloing information:
```
MAJOR=16
MINOR=45
BUILD=421
PATCH=19
```


# Reference
* https://github.com/anawhj/jRound

# Tips
## List up applicaitons in Android
```
$ adb shell 'pm list package -f' 
$ adb shell pm uninstall -k com.joone.rd
```
