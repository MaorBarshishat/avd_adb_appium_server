    # Android Virtual Device - Android Debugger Brigge - Appium Server 

This program has 2 main parts that working combined - android virtual device (avd), and appium server, they connected in a way that called "android debugger bridge" (adb).

### Objectives Of Each Part:
- **Android Virtual Device:** defines the characteristics of an Android phone, tablet, Wear OS, Android TV, or Automotive OS device that you want to simulate in the Android Emulator.<br/>
For our mission, it is used to imitate telegram application on Android device, it receives commands from the automation testing, and communicate withe the telebot through Telegram's network.
- **Appium Server:** is an HTTP server that facilitates mobile app testing by managing communication between test scripts and devices.<br/>
Its objective is to connect between the unittest program to the AVD, basiclly it converts python commands to the device.

It can be deployed as a docker, or being installed on the host.

### as a docker:
Please note that I am using a 3rd party docker.
```
    sudo docker run --privileged -d -p 6080:6080 -p 5554:5554 -p 5555:5555 -p 4723:4723 -e DEVICE="Samsung Galaxy S6" -e APPIUM=True --name android-container butomo1989/docker-android-x86-7.1.1
```
After executing this command, follow these steps to perform the tests:


The following sould be done once per the docker execution (not per test). It is expected to have it running without restarting.
In a future release I will build a docker with all the following requirements built-in the docker.

1. **Access the Virtual Device using novnc:** Enter the URL `http://{IP address}:6080/` to view the virtual device. the IP address will typically be 172.17.0.2, but this depends on many other factors may be a different address.
2. **Download Telegram:** In the novnc window, enter the phone browser and search for "Telegram" and select "Telegram for Android" (accept the terms).
3. **Install the Application:** Once downloaded, swipe down from the top of the screen and tap on the download notification to install the application.
4. **Log In:** Open the Telegram app and log in with a real user account (e.g. yours).
5. **Prepare for Testing:** We need to have a jpeg and a non-jpeg files on the device to apply the testing. For this, exit the application and navigate to the camera. Take **one photo** and **one video**.
6. **Interact with the Bot:** In order to have clean tests it is required to initially accept terms and some access grants. Return to Telegram, search for `@maor_practice_bot` (it is the bot account), enter the chat, say "hello," and send the photo to the bot (accept any terms as needed). After sending the photo to the bot you will receive a hash value, please copy the value which will later be provided to the client.
