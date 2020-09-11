# AnC-FCMDebug-Android

[![N|Solid](http://artsncode.com/wp-content/uploads/2019/06/Artboard-2.png)](https://nodesource.com/products/nsolid)

Arts'N'Code Firebase Cloud Messaging Debug is an android debug application that is used to easily test your firebase notifications.

  - Simple app layout
  - Grabs the device's firebase token (Instance ID)

# How-To

  - Clone this repository
  - Sync Gradle
  - Open Gradle toolbar at the right of the Android Studio window
  - Run FirebaseNotificationTeste -> Tasks -> android -> signingReport
  - When the script finishes running you should be able to see the signing log in Android Studio
  - Copy the SHA1 key since we will need it in a later step
  - Goto [Firebase Console](https://console.firebase.google.com/)
  - Add a new project (or use your existing project)
  - Once your project is ready go to your firebase project settings and add a new android app
  - Set the Android Package Name to: `com.artsncode.firebasenotificationtester`
  - Set the Debug Signing Certificate SHA-1 to the key from the Gradle signing report we got earlier
  - Click on Register App
  - Download `google-services.json` and save it in the project's directory in `app/google-services.json`
  - And that's it you are all set


# Next Steps
  - You should be able now to send notification either by using the firebase console or by using their SDK/API
  - You can also use the app as a sandbox for grabbing and manipulating the received notifications

### Send Notification to a Single Device
  - The application already has a button that when clicked it logs your device's firebase token (Instance ID)
  - Just click on the button and you should be able to see your token in the logcat
  - Copy the token and head over to the Cloud Messaging section in the firebase console
  - Click on send message
  - Set the title and body of your message then you should see a button on the right that says `Send Test Message`
  - Click on that and paste your token then click on `Test`
  - And that's about it you should receive a notification on that device

# Q&A
  > **Q**: I am only receiving a notification when the app is in the background, why?
  > **A**: This is normal since by default the firebase android SDK only handles notifications and shows them to you when the app is in the background. If you need to handle messages in the foreground then you will need to override the `FirebaseMessagingService` class and add your logic in `onMessageReceived()` method.
  
  > **Q**: I am not receiving notifications at all, why?
  > **A**: Make sure to follow all the steps again and carefully, if that also did not work then create an issue with all the required information so that others can help you out.

