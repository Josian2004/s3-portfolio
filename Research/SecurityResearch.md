# How can I prevent unauthorized people from using my server?

## Why is it a problem?
Currently, there is no way that I know for sure that the application connected to my server is the Minecraft Server, theoretically, anyone could open a WebSocket connection to my server and act as the Minecraft server to send fake data. This would result in inaccurate information about computers and is in general a big problem. 

In the future I also want to give users of my website the ability to directly control turtles, think of turning them on/off, controlling the movement, rebooting them, etc, but I only want to give the MCS Players the ability to do this, not every random visitor should be able to directly control the turtles and can take every system offline.

In conclusion, at the moment, every random visitor or person who knows the URL of my WebSocket could take full control over the send data and the turtles in the Minecraft Server while only the Minecraft Server itself or MCS Players should have this ability so it is a pretty big problem.

## What are the things I can do to prevent it?
### Authentication/Authorization
The best way to prevent unauthorized access is to implement an authorization system so that users (and the Minecraft Server) need to verify that they are authorized to use the API.

A way to do this is with tokens, tokens are unique, randomly generated strings that are given to authorized clients to grant access to the API. A client must first request a token from an authentication server, this is done by securely sending a username and password to an endpoint of the said authentication server. The server then validates the credentials and returns a token if valid.

The client can then use this token to make authorized API requests, they will include the token in the header of the request. The server will then check if the received token is valid and if they are authorized to use the API, to do this the server will send the token to the authentication server and which will tell if the token is valid and if they are authorized. If that is the case the API will allow the request but if the token is invalid or expired, it will deny the request and return a '401' code, this means UNAUTHORIZED and then the client will know why its request was denied.

In summary, this will prevent random people, with knowledge of the API/WS URLs, from accessing the API to send and receive data. Now a client (Minecraft Server or MCS Player) will need to verify who they are to do things like send computer info, locations, messages etc and control the turtles. But hackers could still intercept the token and use it for themselves but this can be fixed with SSL.

### SSL
SSL (Secure Sockets Layer) is a security protocol that provides secure communication over the internet, it uses public key and symmetric key encryption to secure and encrypt the data sent between a client and a server.

To secure an API with SSL, you will need an SSL certificate from a certificate authority, once obtained, you will need to install this certificate somewhere on your server and configure your API (NGINX in my case) to use this certificate.

When your server has an SSL certificate, you can use HTTPS to access the API instead of the standard HTTP. With HTTPS all the traffic between the client and server and secured and encrypted so that nobody can intercept the request and alter its contents (Man-in-the-Middle (MitM) attack), this will thus also prevent your token from being stolen and used for unauthorized access.
### Rate limiting
Another way to secure an API is rate limiting, this is a technique to limit the number of requests a client can make in a given period. It is most often used to secure the API against DoS (Denial of Service) attacks. An example of rate limiting is setting a limit of 1000 requests per hour, this means that the client can make up to 1000 requests and if the client surpasses the limit the requests will be denied until the period expires.

## How will I implement it in my own application?
### MCSAuth (Authorization)
We have created our own authorization service called 'MCSAuth', we can use this server to verify that the user is a valid MCS player or the actual Minecraft server. Every player has their login credentials which they can use to request a token from our authorization server, this token is then saved as a cookie in the browser and can be used on every mcsynergy.nl website to authenticate. Whenever the user wants to do something authorized, the browser will send their token with the request and the server will then validate the token and return the requested data if valid.

The Minecraft server itself also has its own login credentials, we have a computer in our server which can request a token from our authorization server. Every other computer/turtle in the server can then use this token to validate themselves. This makes sure that the Minecraft server connected to my server is the MCSynergy server and not a random user with Postman.

This whole system makes sure that data is only returned if the client is an authorized MCSynergy player or server, so unauthorized people are unable to request or send fake/malicious data to my server.
### SSL
The previous solution only prevents unauthorized clients from directly getting the data, but they can still easily intercept the data, to solve this I need to encrypt the network traffic between the clients and my server. 

I've done this by installing an SSL certificate on my server using Certbot and LetsEncrypt, I've configured my NGINX to use these certificates and force all traffic from HTTP to HTTPS. Now whenever someone communicates with my server the request goes over HTTPS and is thus encrypted, other people are then unable to see the data. This also works with WebSockets, using an SSL certificate, the WebSocket will use the WSS protocol (instead of WS) which also encrypts all the data transmitted over the WebSocket.
## Conslusion
The best way to prevent unauthorized access to my server is by implementing a token-based authorization/authentication service, this makes sure that the client is a valid MCS Player or server and not a random person. To prevent people from intercepting the token and using it for themselves, I will be using an SSL certificate to encrypt all the data. I don't think that rate limiting is very useful in my situation, my application will only be used by MCS players and won't be publicly known so it isn't a very big target for DoS attacks and I trust that the MCS players won't DoS attack my server. If the application will be used by more people, it is a good solution to implement.
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
