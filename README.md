    # Android Virtual Device - Android Debugger Brigge - Appium Server 

This program has 2 main parts that working combined - android virtual device (avd), and appium server, they connected in a way that called "android debugger bridge" (adb).

### Objectives Of Each Part:
- **Android Virtual Device:** defines the characteristics of an Android phone, tablet, Wear OS, Android TV, or Automotive OS device that you want to simulate in the Android Emulator.<br/>
For our mission, it is used to imitate telegram application on Android device, it receives commands from the automation testing, and communicate withe the telebot through Telegram's network.
- **Appium Server:** is an HTTP server that facilitates mobile app testing by managing communication between test scripts and devices.<br/>
Its objective is to connect between the unittest program to the AVD, basiclly it converts python commands to the device.

It can be deployed as a docker, or being installed on the host.
Here I am focusing on docker installation.

### as a docker:
```
   sudo docker network create --subnet=172.18.0.0/16 net_maor
   sudo docker run --privileged -d -p 6080:6080 -p 5554:5554 -p 5555:5555 -p 4723:4723 -e DEVICE="Samsung Galaxy S6" -e APPIUM=True --net net_maor --ip 172.18.0.2 --name android-container-maor maorbarshishat/appium_android_maor:3.0
```
note: if net_maor was already created, an error message will appear, so plz ignore it.

It is possible to view the testing process through novnc. to do that please connect http://172.18.0.2:6080 from a browser on the local host.
