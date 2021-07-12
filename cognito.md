# Research for Amazon Cognito

## Terms to Know
**Authentication**

The process of verifying someone's identity usually with a username and a password

**Authorization**

The process of granting users access to specific resources after they have been authenticated. Users may be placed in one of more groups based on their job title and the application then determines which features are available to them based on their group membership.

**Identiy Providers**
A service that manages authentication, providing a user login and the ability to verify a user's identity. AWS Cognito has itz own Identity Provider (using User Poools) but can also integrate with well-established third party Identity Providers like facebook and Google. 

**IAM**
IAM role is an AWS Identity and Access Management entity wth permissions to make AWS service requests. IAM roles cannot make direct requests to AWS service;they are meant to be assumed by authorized entities such as IAM users, applications or AWS services such as EC2. 



**Federation**
Process of integrating with a third-party for authentication. 

## AWS Cognito
Amazon Web Services' service for managing user authentication and access control. Comprised of two separate but related services: User Pools and Identity Pools (also called Federated Identities)

**User Pools** provide a user directory for your application including sign-up, sign-in, group management, etc. Also provide app with info on user's ID and group membership so that your code can handle authorization. 

**Identity Pools** are used to assign IAM roles to users who authenticate through a separate Identiy Provider. Because these users are assigned an IAM role, they can have their own set of IAM permissions, allowing them to access AWS resources directly. 

- map a user from an Identity Provider to an IAM Role, allow you to delegate authorization for AWS resources to AWS itself 

User Pools by themselves don't deal with permission at the IAM-level. Rather they provide information like group memebeship and the user's ID to your app, so you can deal with authorization yourself. 

Identiy Pools in contrast grant users permisssions at the IAM level.  This means that idenity pools allows for more granular set of permission with respect to AWS services. 
Remember main purpose of an idenity pool is to map user from an idenity provider to an IAM role. It does not have its on user directory, it just assigns users from other user directories to an IAM role in your AWS environment. 

Often the Identity Provider is a thirdy party but it can also be your app's own user directory if its implemented as a Cognito User Pool. You can configure your identty pool to use your app's own user pool as one of its idenity providers. This gives you the ability to authenticate users with your User Pool and assign them an IAM role using an Identity pool.

Remeber the key distinction is not whether the Identity Provider is internal or external but rather if an IAM role is assigned to the user after authentication. 

## When designing Cognito Arch Ask
1. Whether it makes sense to manage security at the IAM level. If you have important AWS resources whose access can easily be segreate using IAM pemrission, then consider using Identity Pools
    - Ex. if you store confidential info in s3 and ach bucket stores info for a different department then it might makes sense to use idenity pools to let AWS manage access to those buckets via IAM. But if most of the info resides in a db, then IAM permissions won't help much, as they don't provide row or column level granularity, only application code can do that
2. Determine whether your application needs to integrate with third party idenity providers. if its small internal business app, you likely don't need third party. If your app is public and consumer facing website, that promotes self-registration then giving the ability toregiser with an existing social is a must have 
3. Consider tradeoff between coplexity and security.  The more services the more complexity. 
    - Ex1. user ppol with no third party integration
    - Ex2. highly conifidential finacial data that needs to be secure that may need to be accessed for external parties, then you should manage access at the application level AND the IAM level. This requirs, User Pools, Federated identities, and highly granular IAM permissions. 


Resources: https://thenewstack.io/understanding-aws-cognito-user-and-identity-pools-for-serverless-apps/

## Cognito Design
Pricing

-  User Pool has a free tier of 50,000 MAU (Monthly Active Users) and 50 MAUs for users federated through SAML 2.0 based identity providers. 
For users signing in with credentials from a user pool or with social idenity providers like googe, twitter, there are volume based pricing tiers for MAUs above the free tier.

|Pricing Tier (MAUs) | Price per MAU|
|--------------------|--------------|
|50,001-100,000 (after the 50,000 free tier)|	$0.0055|
|Next 900,000	|$0.0046|
|Next 9,000,000	|$0.00325|
|Greater than 10,000,000|$0.0025|

### Questions
- Difference between a group and a IAM role
- How many groups should we have. Initial thoughts
    - user
    - admin (devs, analysts, etc)
    - super-admin (manager-level) 
- should other attributes be added/collected when a user joins. (State they belong to?)
- what is AWS cloud formation?
    - service that helps you model and set up your amazon web services reousrces so that youcan spend less time managing those resources and more time focusing on your applications that run in AWS. 

### Things to remember/learned
- When setting up phone numbers, need to include +\<areacode> (remember for when you ask Derrick for list of alpha users)
- 
