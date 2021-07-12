# More on Authentication

Multifactor Authentication of MFA is an authenticationmethod that requires the user to provide two or more verification factors to gain access to a resource such as an applicaton, onine account or VPN. Core component of idenity and access management (IAM)

IAM or idenity and access management ensures the right people and job roles can access tools they need to do their jobs. 

## How does it work?
1. IAM confirms that the user, software, or hardware is who they say they are by authentcating their credentials against a database. IAM cloud identity tools are generally more secure
2. IAM systems grant only the appropriate level of access. Instead of username + password, IAM allows for certain levels of access, ie editor, viewer,  etc. 
Ex Flow. User signs in with username password, backend checks a database and sees if they're approve, if so great we move on if not, denyyy. 

IAM 
- manages user idenities
- porvision/ deporvision users
- authentice users
- authorize users
- reporting
- single sign-on

https://www.onelogin.com/learn/iam

## Single Sign on
https://www.onelogin.com/learn/how-single-sign-on-works 

SSO works like a trust relationship between an app (service provider) and an idenity provider (Amazon, Google, Facebook, etc). Trust often based on a cert that is exchanged between idenity provider and service provider. In SSO, identity data is in the form of tokens which identify the user. 

SSO Flow
1. user goes to app or website
2. app or website sends a token that contains info about user to SSO system, the identiy Provider, as part of request to authenticate user. 
3. IP checks if user already has been authenticated. If so, skip to 5
4. user is prompted to log in. 
5. once IP validates credentials, it will send token to service provider or app confirming successful authentication
6. token passed through the users browser to service provider
7. token received by service provider
8. user granted access. 

There are SSO solutions vs providers vs software. 

