# How do push notifications work

## What are push notifications?

A push notification is a small message that pops up on a mobile device, the message is always from an downloaded app. Developers use push notifications to instanly inform the user about something, this could be when your favourite soccer team scores or when your train is delayed. Studies have shown that someone is 2x more likely to interact with their phone when a message is shown as a push notification than as an email, thats why more and more developers are using push notifications over emails.

## But how do they work?
Push notifications are not as straight forward as you might think, the app itself is never the receiver of a push notification.

Mobile devices use an OSPNS (Operating System Push Notification Service) to receive notifications, this is an service which is responsible for sending the actual push notifications to a device. Each operating system has their own OSPNS, Apple has APNs and Google has FCM. Apple was actually the first to introduce an OSPNS and Google then quickly followed.

When a user downloads your app, he will be prompted to give permission to receive notifications. When permission is given, the app will receive a unique token from the operating systems OSPNS and this token is then sent to the back-end server of the downloaded application. The developer itself is responsible for saving these tokens, [Google has some best practises on how to manage these tokens](https://firebase.google.com/docs/cloud-messaging/manage-tokens). Some of these best practises are: Save the token with a timestamp so you know when it was the last time that a device was online, Google recommends that tokens are deleted when they are inactive for more than two months, and when the server tries to sent a notification to an inactive/invalid token, the api will return a 400 or 404. When this happens the server should automatically delete this token because it will never be active again

## Sources
- https://developer.apple.com/documentation/usernotifications
- https://firebase.google.com/docs/cloud-messaging
- https://www.airship.com/resources/explainer/push-notifications-explained/
- https://onesignal.com/blog/what-is-a-push-notifications-service-and-how-does-it-work/
