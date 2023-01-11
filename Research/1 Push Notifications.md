# How do push notifications work

## What are push notifications?

A push notification is a small message that pops up on a mobile device, the message is always from a downloaded app. Developers use push notifications to instantly inform the user about something, this could be when your favourite soccer team scores or when your train is delayed. Studies have shown that someone is 2x more likely to interact with their phone when a message is shown as a push notification than as an email, that's why more and more developers are using push notifications over emails.

## But how do they work?
Push notifications are not as straightforward as you might think, the app itself is never the receiver of a push notification.

Mobile devices use an OSPNS (Operating System Push Notification Service) to receive notifications, this is a service which is responsible for sending the actual push notifications to a device. Each operating system has its own OSPNS, Apple has APNs and Google has FCM. Apple was the first to introduce an OSPNS and Google then quickly followed.

When a user downloads your app, he will be prompted to permit to receive notifications. When permission is given, the app will receive a unique token from the operating system OSPNS and this token is then sent to the back-end server of the downloaded application and the OSPNS. Every time the app is started, it should send its token to the servers to refresh it, this will make sure that a token is always valid. This token might change after an update, redownload or the deletion of its cache.

The developer itself is responsible for saving these tokens, [Google has some best practices on how to manage these tokens](https://firebase.google.com/docs/cloud-messaging/manage-tokens). Some of these best practices are: Save the token with a timestamp so you know when it was the last time that a device was online, and Google recommends that tokens are deleted when they are inactive for more than two months. When the server tries to send a notification to an inactive/invalid token, the API will return a 400 or 404. When this happens the server should automatically delete this token because it will never be active again.

Now that the tokens are saved in the back end, the developer can use these to send notifications to specific users. When the server wants to send a notification, it will send an HTTP POST request to the OSPNS API with the device token(s) and the notification itself. The OSPNS will then receive the notification and redirect it to the corresponding devices. The OSPNS has a constant WebSocket connection with the device, this connection is then used to send the notification. Depending on the priority of the notification, this WebSocket connection refreshes more often and notifications are delivered faster but this also uses more of the battery of the device. The higher priority is mostly used for applications like chat apps where the user should be immediately notified.

## What does a push notification look like?

You can't just send some text to an API, the notification should be of a specific JSON format. Otherwise, the ASPNS won't recognize that it is a notification. The code below is an example of a notification in a JSON format, this one is used for FCM.

```json
{
    "to": "<DEVICE_TOKEN>",
    "collapse_key": "type_a",
    "notification": {
        "body": "Test 4 Notification",
        "title": "Test 4",
        "sound": "default",
        "content_available": true,
        "priority": "high"
        
    },
    "data": {
        "body": "Test 4 Notification",
        "title": "Test 4",
        "sound": "default",
        "content_available": true,
        "priority": "high"
        
    }
}
```
The "to" key is the device token that the developer should have saved somewhere in a database, it is used to identify a device so the ASPNS knows to what device it should send the notification.

"collapse_key" is used for refreshing a notification. E.g. a notification with a message about an ongoing sale is sent, this sale is only valid for the next 5 hours but the user doesn't receive the notification in this timespan. After those 5 hours, the server sends another notification with the same tag, because of the collapse_key, the previous notification will be overwritten by the new notification so the user only receives the last one.

Then we have two objects, a notification and a data object. The notification is for the push notification itself, so that's what the user will see on their screen. The data is for the app itself, it can use the given data to do something with it. E.g. the developer wants that when a notification with the title of the data object as "blue" is sent, the app changes its colour to blue. You can also use the data object to send custom keys and variables that won't be shown in the push notification.

In these objects, we have some pretty self-explanatory keys like the title, the title of the notification, the body, the body text of the notification and the sound. There is also a priority key, here you can enter either "normal" or "high". With "normal" there might be a delay of a few minutes before the notification is delivered, while with "high" the notification is almost instantly delivered. "High" however does use more battery.


## Comparing Apples to Androids
What is the actual difference between the OSPNS of Apple and Google?
Both Apple and Google have their OSPNS, and they have the same purpose but there are some differences between these two. Apple released APNs in 2009 and Google followed with their GCM in 2010, in 2014 the core infrastructure of GCM was moved to Firebase and then renamed to FCM.

### Differences
#### Accounts
One major difference is that for APNs (and FCM with iOS) you need an Apple Developers Account which you can buy for $100/year. FCM for Android however is completely free of charge.

#### Notification Format

They use a different format for sending notifications. APNs send notifications as strings or dictionaries, these contain sound, badge, token, body and title. FCM on the other hand uses JSON to send notifications as seen in the example above.

#### Payload

There is a difference between payload sizes. With APNs you can send a notification up to 4 KB (only 256 bytes before iOS 8) while FCM only allows notifications up to 2 KB. However you can also send messages with FCM, these can be up to 4 KB.

#### Storage of notifications
Both services store notifications when the receiving device is offline or is unable to receive notifications, they do however store them differently. APNs store one notification per app, so if the app receives a second notification the first one is overwritten. FCM doesn't store notifications per app but stores 100 notifications per device. For both services, notifications are saved for a maximum of 28 days.

#### Cross-platform
APNs only support iOS, macOS, iPadOS and watchOS while FCM supports both iOS and Android.

## Sources
- https://developer.apple.com/documentation/usernotifications
- https://firebase.google.com/docs/cloud-messaging
- https://www.airship.com/resources/explainer/push-notifications-explained/
- https://onesignal.com/blog/what-is-a-push-notifications-service-and-how-does-it-work/
- https://www.hexnode.com/blogs/comparison-apple-push-notification-service-apns-gcm-fcm-wns/
