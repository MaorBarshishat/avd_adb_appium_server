# Android Virtual Device - Android Debugger Brigge - Appium Server 

This program has 2 main parts that working combined - android virtual device, and appium server, they connected in a way that called "android debugger bridge".

### Objectives Of Each Part:
- **Android Virtual Device:** s a configuration that defines the characteristics of an Android phone, tablet, Wear OS, Android TV, or Automotive OS device that you want to simulate in the Android Emulator.
  His objective is to imitate telegram application and make conversation with the bot - testing.
- **Appium Server:** Appium Server is an HTTP server that facilitates mobile app testing by managing communication between test scripts and devices.
  His objective is to connect between the unittest program to the AVD, basiclly its converts python commands to the device.

### as a docker:
```
sudo docker run --privileged -d -p 6080:6080 -p 5554:5554 -p 5555:5555 -p 4723:4723 -e DEVICE="Samsung Galaxy S6" -e APPIUM=True --name android-container butomo1989/docker-android-x86-7.1.1
```
After executing this command, follow these steps to perform the tests:

1. **Access the Virtual Device:** Enter the URL `http://172.17.0.1:6080/` to view the virtual device.
2. **Download Telegram:** In the browser, search for "Telegram" and select "Telegram for Android" and install (accept the terms).
3. **Install the Application:** Once downloaded, swipe down from the top of the screen and tap on the download notification to install the application.
4. **Log In:** Open the Telegram app and log in with your user account.
5. **Prepare for Testing:** Exit the application and navigate to the camera. Take **one photo** and **one video** (this is crucial for the tests).
6. **Interact with the Bot:** Return to Telegram, search for `@maor_practice_bot`, enter the chat, say "hello," and send the photo to the bot (accept any terms as needed).
