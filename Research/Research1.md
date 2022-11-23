# How do push notifications work

## What are push notifications?

A push notification is a small message that pops up on a mobile device, the message is always from an downloaded app. Developers use push notifications to instanly inform the user about something, this could be when your favourite soccer team scores or when your train is delayed. Studies have shown that someone is 2x more likely to interact with their phone when a message is shown as a push notification than as an email, thats why more and more developers are using push notifications over emails.

## But how do they work?
Push notifications are not as straight forward as you might think, the app itself is never the receiver of a push notification.

Mobile devices use an OSPNS (Operating System Push Notification Service) to receive notifications, this is an service which is responsible for sending the actual push notifications to a device. Each operating system has their own OSPNS, Apple has APNs and Google has FCM. Apple was actually the first to introduce an OSPNS and Google then quickly followed.

When a user downloads your app, he will be prompted to give permission to receive notifications. When permission is given, the app will receive a unique token from the operating systems OSPNS and this token is then sent to the back-end server of the downloaded application and the OSPNS. Every time the app is started, it should sent its token to the servers to refresh it, this will make sure that a token is always valid. This token might change after a update, redownload or the deletion of its cache.

The developer itself is responsible for saving these tokens, [Google has some best practises on how to manage these tokens](https://firebase.google.com/docs/cloud-messaging/manage-tokens). Some of these best practises are: Save the token with a timestamp so you know when it was the last time that a device was online, Google recommends that tokens are deleted when they are inactive for more than two months. When the server tries to sent a notification to an inactive/invalid token, the api will return a 400 or 404. When this happens the server should automatically delete this token because it will never be active again.

Now that the tokens are saved in the back-end, the developer can use these to sent notifications to specific users. When the server wants to sent a notification, it will sent a HTTP POST request to the OSPNS API with the device token(s) and the notification itself. The OSPNS will then receive the notification and redirect it to the corresponding devices. The OSPNS has a constant websocket connection with the device, this connection is then used to sent the notification. Depending on the priority of the notification, this websocket connection refreshes more often and notifications are delivered faster but this also uses more of the battery of the device. The higher priority is mostly used for applications like chat apps where the user should be immediatly notified.

## What does a push notification look like?

You can't just sent some text to an API, the notification should be of a specific JSON format. Otherwise the ASPNS won't recognize that it is a notification. The code below is an example of a notification in a JSON format, this one is used for FCM.

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
The "to" key is the device token which the developer should have saved somewhere in a database, it is used to identify a device so the ASPNS knows to what device it should sent te notification to.

"collapse_key" is used for refreshing a notification. E.g. a notification with a message about an ongoing sale is sent, this sale is only valid for the next 5 hours but the user doesn't receive the notification in this timespan. After those 5 hours the server sents another notification with the same tag, because of the collapse_key, the previous notification will be overwritten by the new notification so the user only receives the last one.

Then we have two objects, a notification and a data object. The notification is for the push notification itself, so thats what the user will see on their screen. The data is for the app itself, it can use the given data to do something with it. E.g. the developer wants that when a notification with the title of the data object as "blue" is sent, the app changes it's color to blue. You can also use the data object to sent custom keys and variables that won't be shown in the push notification.



## Sources
- https://developer.apple.com/documentation/usernotifications
- https://firebase.google.com/docs/cloud-messaging
- https://www.airship.com/resources/explainer/push-notifications-explained/
- https://onesignal.com/blog/what-is-a-push-notifications-service-and-how-does-it-work/
