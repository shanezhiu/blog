Title: App Security: Why is it worth to implement JWT based authentication into your app?
Category: Programming
Tags: Security,http,APP Design,tech,reprinting
Slug: why-is-it-worth-to-implement-JWT-based-authentication-into-your-app
Lang: en


> Origin Url:[App Security: Why is it worth to implement JWT based authentication into your app?][1]

__App speed and security are of huge importance. Our main goal aligned with our customer’s goal is to deliver a satisfactory product as quickly as possible and within budget. There are a number of practices, recommendations and even proposals on how to run projects, but implementation details are extremely important – small changes that allow us to write competitive applications.__

__When creating a web service one of the most important things is choosing the right authorization method.__There are a number of choices: [OpenID][2], [SAML][3], [Kerberos][4] and [OAuth2][4] which is the most popular open standard authorization framework. The authorization process for OAuth2 consists of sending the client an authorization request with credentials to issue a random token from the authorization server. This is sent to the resource server to verify if the client is authorized to use the resource and perform specific operations.


__The framework is supported by [Microsoft][6] (for several APIs and Azure Active Directory service), [Facebook][7] (only GraphAPI__ – the primary way for apps to read and write to the Facebook social graph) and [Google][8] (__authorization mechanism for every their APIs__). The fact that OAuth2 is used by such important companies in the IT market, vouches for the quality and benefits of this method. In most cases a username and token are required in OAuth2, and additionally it specifies the way in which the tokens are to be sent… and this is where __[JWT][9] (JSON Web Token)__ comes forward. __JWT is not a protocol or an authorization framework, but it determines the format of the authorization token, which, as it turns out, can have a measurable impact on the functionality of the entire mechanism.__

## Why is JWT gaining so many supporters
**JWT became an open standard in 2015**, and in the same year **RFC** was also created for **JSON** Web Token Profile for **OAuth 2.0** Client Authentication and Authorization Grants, suggesting the possibility of using the **OAuth2** protocol with the **JWT** format for tokens. It gained many fans because of its simplicity and ease to use. As the name suggests, the format of the token is presented in **JavaScript Object Notation (JSON)**. It is a very common data format used for communication between the browser and the server. Thus giving the opportunity for a concise and clear way of transferring information between the two parties in a JSON object. Further, thanks to the huge amount of parsers available in the programming languages, we can directly convert the received token into an object. __It is also worth comparing it to other popular formats such as SAML, SWT or even ordinary string UUID__. As for the structure, it is more concise, we do not need to convert a huge token presented in the form of XML as in the case of SAML (obviously the problem concerns front-end site). **However, the biggest advantage is the possibility of transferring a large amount of additional information in one token, a so-called claimsy.** Support in the form of a huge number of token signing and token verification libraries for virtually any programming language suggests the usability of JWT on a large scale while maintaining an 

## What can we pass
**A big advantage is the ability to format JWT claims transfer in a token.** Claims are statements about an entity (typically, the user) and additional data. Additional token content allows you to limit the number of database queries. Only basic information about the user is collected at the moment of logging in. It should also be noted that the format works well in the context of microservices. It is possible to transfer data between microservices without having to ask for data from a central session microservice. As such if the signature is correct, then the received data is also reliable and we can be trusted.

![1](/images/20190826/grafika_2d.jpg "What can we pass")


__Let’s analyze the content of individual elements of a JWT token, in particular the Payload, which contains our additional information:__

**Header** – informs about the algorithm that was used to generate the token (the standard defines algorithms such as HMAC SHA256 RSA)

**Signature** – is the digital signature of our token, encrypted in Base64 and calculated from combination of the Header and Payload together with the secret key – in our case the hash function is HMAC-SHA256.

**Payload** – the content looks familiar to a typical response in JSON format to a specific resource in REST services. Creating claims can be compared to the preparation of a DTO (Data Transfer Object). Set of information to be returned within the token is defined in the server code. As you can see in the example above – information about the user’s hobby, country of residence, the currency in which he performs his transactions and standard user’s information of the system – id, username and its roles will circulate in the token. It is not a coincidence that I pointed out the types of claims … it is worth stressing that you have to use your own claim names carefully because they may already be registered in iana.org and cause name conflicts. In the example, we’re using two reserved claims – exp (token expiration time) and jti (token id to prevent repetition).

## Security
**Security is often associated with hiding all data. The JWT standard does not encrypt data**, but only converts it to Base64. The creators’ assumption is to be sure that the data being sent to the authorization server is created by a reliable source, thus – preventing unauthorized access. This is why it’s also worth to encrypt the data using SSL protocol to prevent theft of the token. The most important thing is that we are sure about the sender’s identity and that the data received has not been compromised in any way. Verification of the token is quite simple.
![1](/images/20190826/grafika-1.jpg "Security")


**Servers have secret keys and use them to generate a JWT token**. This is of great importance, as because of this they are able to verify its correctness. If the credentials match a **JWT** token is generated at the request of the client. Thanks to the fact that the application server knows the secret key, it can generate a signature for the **JWT** token received from the user and compare it with the signature. If everything goes correctly, the user is authenticated and can accesses certain data. Otherwise it may indicate some kind of attack. Thanks to this, access to resources on the server is safer, particularly because authentication with user credentials is a one-time process.


## Microservices
**It would be a sin not to mention microservices**. Especially that **JWT** is doing so well within this architecture. At this point, it is worth distinguishing between two approaches: writing monolithic applications and those based on microservices that are independent of each other.

**Protection for monolithic applications is quite simple**. There is an application server that manages user authorization and authentication in advance. In addition, we are sure that all services on which we perform queries are implemented on one and the same server. We do not need to worry about whether each service has authenticated the user separately. It is fully decentralized.

Microservices are different and the main problems are the communication between them and the answer to the question: “*__How can we authenticate the user and be sure that other microservices know about it?__*“ As it turns out, JWT ensures that we send information between all microservices about the fact that a given user has access to specific resources.

We use the OAuth2 credential grant (*__client credential grant__*) that allows clients to obtain access tokens by providing their client id and secret. As a result, each microservice receives its own client identity and credentials. Then, this data is sent along with the request for token access to the authorization server.

**The advantage of this solution is that you can withdraw access to the microservices at any time if we verify the user’s password has been compromised.** In addition, the management of scopes, roles, and credentials of microservices are completely controlled. Thanks to JWT claims (more precisely the permissions contained in the token) we know exactly to which resources the user has access, which makes JWT a perfect fit for such architecture.
![1](/images/20190826/2764.jpg "Microservices")

## Summary
**The JSON Web Token is an increasingly popular format for representing tokens;** it is slowly becoming a standard token format and the number of users is growing every day. Thanks to its compact size, lightness and independence, it offers great customization possibilities. The token containing all the information needed for verification without a continuous query of the database is amazingly useful. Of course, we can implement a unique solution based on traditional user’s session but this is unnecessary when such a popular solution is in place. Thanks to JWT, we can easily identify the user between particular sites, and the unique session model could not do it better.

[1]: https://espeo.eu/blog/app-security-jwt-based-authentication/ "App Security: Why is it worth to implement JWT based authentication into your app?"
[2]: https://openid.net/ "OpenID"
[3]: https://www.samltool.com/ "SMAL"
[4]: http://web.mit.edu/kerberos/ "Kerberos: The Network Authentication Protocol"
[5]: https://oauth.net/2/ "OAuth 2.0"
[6]: https://www.microsoft.com/pl-pl/ "Microsoft"
[7]: https://facebook.com/ "facebook"
[8]: https://google.com/ "Google"
[9]: https://jwt.io/ "JWT"