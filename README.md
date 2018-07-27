# ChatApp

This project was created by me and my team during the Java Enterprise module of Codecool. We had roughly 1 and a half week-long sprint plan and implement an application of our choosing, which turned out to be a chat app based on Discord. Features include a lobby, chat rooms and private chatting with logged-in users.

# Backend

There are two different microservices behind the Angular SPA:

1. A [Java8 based framework](https://github.com/CodecoolBP20173/MNG-chat-app) of my teammate [Daniel Csaszar](https://github.com/DanielCs1988), providing a WebSocket server for transmitting messages.
2. A [Spring API for chat history](https://github.com/CodecoolBP20173/Hermes-MNG), users profiles and rooms details.
Both applications use the same PostgreSQL database, even though most of the heavy lifting is done by Spring on the data part.

Authentication and authorization is handled by Spring Security in the Spring API, and with a middleware service in the WebSocket API. An RS256 Json Web Token issued by [Auth0](https://auth0.com/) is passed around to ensure the data and private communications remain secure.


# Frontend
An Angular 6 app communicates with the backends, using both HTTP and WebSocket protocol. The socket channel is controlled by a small frontend library which has been built by my teammate [Daniel Csaszar](https://github.com/DanielCs1988). Logging into the app is possible through OAuth using google accounts, the appropriate JWT is fetched here and then sent with every request using an HTTP interceptor.
