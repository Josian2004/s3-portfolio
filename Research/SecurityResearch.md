# How can I prevent unauthorized people from using my server?

## Why is it a problem?
Currently there is no way that I know for sure that the application connected to my server is actually the Minecraft Server, theoratically anyone could open a WebSocket connection to my server and act as the Minecraft server to send fake data. This would result in inacurate information about the computers and is in general a big problem. 

In the future I also want to give users of my website the ability to directly control turtles, think of turning them on/off, controlling the movement, rebooting them, etc, but I only want to give the MCS Players the ability to do this, not every random visitor should be able to directly control the turtles and have the ability to take every system offline.

In conslusion, at the moment, every random visitor or person who knows the URL of my websocket could take full control over the send data and the turtles in the Minecraft Server while only the Minecraft Server itself or MCS Players should have this ability so it is a pretty big problem.

## What are the things I can do to prevent it?
### Authorization

### CORS

### SSL

### Rate limiting

## How will I implement in in my own application.
### MCSAuth (Authorization)

### SSL

## Conslusion

## Sources
- https://blog.hubspot.com/website/api-security
- https://nonamesecurity.com/learn-rest-api-security
- https://www.f5.com/labs/learning-center/securing-apis-10-best-practices-for-keeping-your-data-and-infrastructure-safe
- https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS
