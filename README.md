# Firebase Integration with Application server


![Firebase Integration](https://github.com/claykabongok/Firebase_Integration/blob/master/readme/App_Firebase_integration%20-%20Android_new.jpg?raw=true)

The following provide some details on how to add the Firebase Admin SDK to your server to send [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging) (FCM)
messages to android devices. I have implemented the following using Java with the [Spring boot framework](https://spring.io/guides/gs/spring-boot/), check the [documentation](https://firebase.google.com/docs) for more details .

I will assume you have completed the following before proceeding: connected your application to [firebase](https://firebase.google.com/docs/admin/setup).

According the [documentation](https://firebase.google.com/docs/admin/setup) the Admin SDK lets you interact with Firebase from privileged environments to perform actions such as reading Realtime Database, programmatically send Firebase Cloud Messaging messages and more.

## Steps to follow:
* Make sure that your server runs the following: Admin Java SDK – Java 7+ (recommend Java 8+), check the documentation for other SDK. The following is also supported Node.js, Python, Go and .NET read the [guide](https://firebase.google.com/docs/admin/setup) for more details.
* Set up a [Firebase project](https://console.firebase.google.com/)  and [service account](https://firebase.google.com/docs/admin/setup#set-up-project-and-service-account)
* [Add the SDK](https://firebase.google.com/docs/admin/setup#add-sdk): install the SDK for the language of your choice in my case java with [Maven](https://mvnrepository.com/) as build automation tool (Add the [firebase-admin dependency](https://mvnrepository.com/artifact/com.google.firebase/firebase-admin) to your pom.xml file).
*  Authentication using [service account](https://console.firebase.google.com/project/_/settings/serviceaccounts/adminsdk): Generate a private key file for your service account (check the documentation for more details), download the JSON file (containing the key)
*  [Initialize the SDK](https://firebase.google.com/docs/admin/setup#initialize-sdk) using the key generated
*  At this stage your App server should be able to connect to Firebase.


### Once you have successfully completed the steps listed, your app server should be connected to Firebase.
 
 ![Firebase Integration](https://github.com/claykabongok/Firebase_Integration/blob/master/readme/App_Firebase_integration%20-%20Android_new.jpg?raw=true)

## The process of sending FCM messages (as illustrated in the diagram above):
1. Device registration: when user installs the app
2. Generate device token: FCM will assign a unique token to each device
3. Upload token to back-end: this allows you to send FCM notification to a specific user depending on your business rules.
4. Send Push notification from trusted application server to FCM with Token (s)
5. Delivers notifications to registered devices
