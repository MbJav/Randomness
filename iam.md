# Understanding IAM

## Terms
IAM resources: user, group, role, policy, and idenity provider objects that are stored in IAM. 

IAM Identities: the IAM resource objects that are used to idenifty and group. You can atach a policy to an IAM identiy. These include users, groups, and roles. 

IAM Entities: The IAM resource objects that AWS uses for authentication. These include IAM users and roles. 

Principal: a person or application that uses the AWS account root user, an IAM user, or an IAM role to sign in and make requests to AWS. Principals include federated users, and assumed roles. 

A requests to make some change includes actions or operations, resources, prinicpal, environment data, and resource data. 

A principal must be authenticated using their credentials to send a request. In this case, from the API you'll need an access key and secret key. You must also be authorized to complete the action. During authroization, AWS uses values from the requests context to check for policies to check for poloicies that apply to the request. Most policies are stored in JSON docs. 

Remember a principal entity is a peson or application that is authenticated using an IAM entity (user or role) (user or role). You manage access in AWS by creating policies and attaching them to IAM identities (users, groups of users, or roles) or AWS resources. A policy is an object in AWS that, when associated with an identiy or resource defines their permissions. 

IAM users are identities in the service. When you create an IAM user, they can't access anything in your account until you give them permission. You give permissions to a user by creating an identity based policy which is a policy that is attached to the user or a group to which the user belongs. 

IAM users can be organized into IAM groups and attach a policy to the group. This way, a user has their own credentials but all users in a group have permissions that areattached to the group.