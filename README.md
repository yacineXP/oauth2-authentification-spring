


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

The project demonstrates how to secure a RESTful API with OAuth 2 using Spring Security. An authorization server is created to authenticate and authorize clients, and a resource server is added to the API to secure the endpoints. The project also shows how to consume OAuth 2–secured APIs.


<div id="code-examples"></div>

## 💻 Code Examples
Here's an example of how to configure an authorization server in Spring Security:
```java
@Configuration
@EnableAuthorizationServer
public class AuthorizationServerConfig extends AuthorizationServerConfigurerAdapter {

    @Autowired
    private AuthenticationManager authenticationManager;

    @Autowired
    private DataSource dataSource;

    @Override
    public void configure(ClientDetailsServiceConfigurer clients) throws Exception {
        clients.jdbc(dataSource);
    }

    @Override
    public void configure(AuthorizationServerEndpointsConfigurer endpoints) throws Exception {
        endpoints.authenticationManager(authenticationManager);
    }

}
```
This code snippet shows how to configure an **authorization server** using Spring Security and the ```@EnableAuthorizationServer``` annotation. The ```@Autowired``` annotation is used to inject dependencies, such as the AuthenticationManager and DataSource.


<div id="acknowledgements"></div>

## 📚 Acknowledgements 
This project was created with the help of the book **"Spring in Action"** by **Craig Walls** and **Ryan Breidenbach**. Many of the concepts and techniques used in this project were learned from this valuable resource.

