


<h1 align="center">
  <br>
<a  href="https://spring.io/"  target="_blank"  rel="noreferrer"> <img  src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg"  alt="spring"  width="180"  height="180"/> </a>
  <br>
  Securing REST API [Learning]
  <br>
  <br>
</h1>

<p align="center">
  <a href="#project-description">Project Description</a> |
  <a href="#tech-stack-and-libraries">Tech Stack and Libraries</a> |
  <a href="#how-it-works">How it Works</a> |
  <a href="#code-examples">Code Examples</a> |
  <a href="#acknowledgements">Acknowledgements</a>
</p>



<div id="project-description"></div>

## 🚀 Project Description
The "o2auth-authentification-spring" project is a demonstration of how to secure a RESTful API with OAuth 2 using Spring Security. It is based on the "Securing REST" chapter of the "Spring in Action" book. The project includes the creation of an authorization server, adding a resource server to an API, and consuming OAuth 2–secured APIs.


<div id="tech-stack-and-libraries"></div>

## 🛠️ Tech Stack and Libraries
- Java Spring
- Spring Security
- OAuth 2
- RESTful API

<div id="how-it-works"></div>

## ⚙️ How it Works

[![Screenshot-from-2023-03-21-11-45-07.png](https://i.postimg.cc/MGhKS9sG/Screenshot-from-2023-03-21-11-45-07.png)](https://postimg.cc/8FmVdmg8)

The project demonstrates how to secure a RESTful API with OAuth 2 using Spring Security. An authorization server is created to authenticate and authorize clients, and a resource server is added to the API to secure the endpoints. The project also shows how to consume OAuth 2–secured APIs.


<div id="code-examples"></div>

## 💻 Code Examples
**1. An example creating a RegisteredClient for OAuth2 Client Registration:**
```java
  @Bean
  public RegisteredClientRepository registeredClientRepository(
          PasswordEncoder passwordEncoder) {
    RegisteredClient registeredClient =
      RegisteredClient.withId(UUID.randomUUID().toString())
        .clientId("taco-admin-client")
        .clientSecret(passwordEncoder.encode("secret"))
        .clientAuthenticationMethod(
                ClientAuthenticationMethod.CLIENT_SECRET_BASIC)
        .authorizationGrantType(AuthorizationGrantType.AUTHORIZATION_CODE)
        .authorizationGrantType(AuthorizationGrantType.REFRESH_TOKEN)
        .redirectUri(
            "http://127.0.0.1:9090/login/oauth2/code/taco-admin-client")
        .scope("writeIngredients")
        .scope("deleteIngredients")
        .scope(OidcScopes.OPENID)
        .clientSettings(
            clientSettings -> clientSettings.requireUserConsent(true))
        .build();
    return new InMemoryRegisteredClientRepository(registeredClient);
  }
```
This code snippet demonstrates how to create a ```RegisteredClient``` object for OAuth2 client registration and define a bean for ```RegisteredClientRepository```. The ```PasswordEncoder``` is injected as a dependency to the ```registeredClientRepository``` method.

The ```RegisteredClient``` object is initialized with a randomly generated ID and the client details such as ```clientId```, ```clientSecret```, ```clientAuthenticationMethod```, ```authorizationGrantType```, ```redirectUri```, ```scope``` and ```clientSettings```.

The ```InMemoryRegisteredClientRepository``` implementation is used to return the ```RegisteredClient``` object.

This code can be used as a reference for implementing OAuth2 client registration in Spring applications.

**2.An exemple of configuring Default Security Filter Chain with OAuth2 Login:**
```java
  @Bean
  SecurityFilterChain defaultSecurityFilterChain(HttpSecurity http) throws Exception {
    http
      .authorizeRequests(
          authorizeRequests -> authorizeRequests.anyRequest().authenticated()
      )
      .oauth2Login(
        oauth2Login ->
        oauth2Login.loginPage("/oauth2/authorization/taco-admin-client"))
      .oauth2Client(withDefaults());
    return http.build();
  }
```
This code snippet defines a ```SecurityFilterChain``` bean to configure the default security filter chain in a Spring application. The ```HttpSecurity``` object is injected as a dependency to the ```defaultSecurityFilterChain``` method.

The ```http``` object is used to configure the authorization and authentication settings for the application. The ```authorizeRequests``` method is used to specify that any request must be authenticated. The ```oauth2Login``` method is used to enable OAuth2 login and set the login page URL to "/oauth2/authorization/taco-admin-clien". The ```oauth2Client``` method is used to configure the OAuth2 client with default settings.

<div id="acknowledgements"></div>

## 📚 Acknowledgements 
This project was created with the help of the book **"Spring in Action"** by **Craig Walls** and **Ryan Breidenbach**. Many of the concepts and techniques used in this project were learned from this valuable resource.

