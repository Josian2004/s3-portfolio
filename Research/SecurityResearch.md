# How can I prevent unauthorized people from using my server?

## Why is it a problem?
Currently there is no way that I know for sure that the application connected to my server is actually the Minecraft Server, theoratically anyone could open a WebSocket connection to my server and act as the Minecraft server to send fake data. This would result in inacurate information about the computers and is in general a big problem. 

In the future I also want to give users of my website the ability to directly control turtles, think of turning them on/off, controlling the movement, rebooting them, etc, but I only want to give the MCS Players the ability to do this, not every random visitor should be able to directly control the turtles and have the ability to take every system offline.

In conslusion, at the moment, every random visitor or person who knows the URL of my websocket could take full control over the send data and the turtles in the Minecraft Server while only the Minecraft Server itself or MCS Players should have this ability so it is a pretty big problem.

## What are the things I can do to prevent it?
### Authentication/Authorization
The best way to prevent unauthorized access is to implement an authoriziation system so that users (and the Minecraft Server) need to verify that they are authorized to use the API.

A way to do this is with tokens, tokens are unique, randomly generated strings that are given to authorized clients to grant access to the API. A client must first request a token from an authentication server, this is done by securily sending an username and password to an endpoint of said authentication server. The server then validates the credentials and returns a token if valid.

The client can then use this token to make authorized API requests, they will include the token in the header of the request. The server will then check if the received token is valid and if they are authorized to use the API, to do this the server will send the token to the authentication server and they will tell if the token is valid and if they are authorized. If that is the case the API will allow the request but if the token is invalid or expired, it will deny the request and return a '401' code, this means UNAUTHORIZED and then the client will know why its request was denied.

In summary, this will prevent random people, with knowledge of the API/WS urls, from accessing the API to send and receive data. Now a client (Minecraft Server or MCS Player) will need to verify who they are to do things like send computer info, locations, messages etc and control the turtles. But hackers could still intercept the token and use it for themselves but this can be fixed with SSL.
### XSS (Cross Site Scripting)

### SSL
SSL (Secure Sockets Layer) is a security protocol that provides secure communication over the internet, it uses public key and symmetric key encryption to secure and encrypt the data send between a client and a server.

To secure an API with SSL, you will need a SSL certificate from a certificate authority, once obtained, you will need to install this certificate somewhere on your server and configure your API (NGINX in my case) to use this certificate.

When your server has an SSL certificate, you can use HTTPS to access the API instead of the standard HTTP. With HTTPS all the traffic between the client and server and secured and encrypted so that nobody can intercept the request and alter its contents (Man-in-the-Middle (MitM) attack), this will thus also prevent your token from being stolen and used for unauthorized access.
### Rate limiting
Another way to secure an API is rate limiting, this is a technique to limit the amount of requests a client can make in a given time period. It is most often used to secure the API against DoS (Denial of Service) attacks. An example of rate limiting is setting a limit of 1000 requests per hour, this means that the client can make up to a 1000 requests and if the client surpasses the limit the requests will be denied until the time period expires.

## How will I implement it in my own application.
### MCSAuth (Authorization)

### SSL

## Conslusion

## Sources
- https://blog.hubspot.com/website/api-security
- https://nonamesecurity.com/learn-rest-api-security
- https://www.f5.com/labs/learning-center/securing-apis-10-best-practices-for-keeping-your-data-and-infrastructure-safe
- https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS
- https://infosec.mozilla.org/guidelines/web_security
- https://owasp.org/www-community/attacks/xss/
- https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html
- https://portswigger.net/web-security/cross-site-scripting
- https://web.dev/strict-csp/
- https://developer.chrome.com/docs/lighthouse/best-practices/csp-xss/
