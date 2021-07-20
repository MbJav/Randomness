# AWS Lambda

### Review
Infrastructure as a Service (IaaS) is a form of cloud computing that provides virtual resources over the internet. It is one of 3 main categories of cloud computing services, alongside software as a service and platform as a service. 

In IaaS, cloud provider (ex AWS) provides the IT infrastructure that would normally live in a data center such as storage, server and networking resources and delivers them to subscriber organization (us) via virtual machines though the internet. 

## Lambda
Lambda is a form of a cloud service tha lets you run code without provisioning or managing servers. Lambda will run your code on a high availability compute infrastructure, administer all the computer resources including automatic scaling, system maintenance, logging etc. 

Code is organized into functionns. You only pay for the ocmpute time that you consume. 

Lambda functions can be called with the Lambda API or Lambda can run your function in response to events from other AWS services. 

### Terms
**Function** is a resource that you can invoke to run your code in lambda

**Trigger** is a resource or configuration that invokes a lambda function. This includes other AWS services that you can confiure to invoke a function. 

**Event** is a JSON formatted document that contains data for a lamdba function to process. The runtime converts the event to an object and passes it to your function. When you invoke a function, you determine the structure and contents of the event. 

**Execution Environment** provides a secure and isolated runtime environment for your lambda function. An execution environment manages the proess and resources that are required to run the function. 

When a Lambda function is invoked, lambda receives the invocation request, validates the permissions in your execution role, verifies that the event document is valid JSON documents and checks the param values. 

If the request is valid, Lambda will send the request to a function instance. Lambda runtime env converts event into an object and passes it to function handler. 

If the handler encounters an error, it returns an exception type, message, and an HTTP status code that indicates the cause of the error. 
- 2xx with X-Amz-Function-Error header indicates an error with lambda runtime. 
- 4xx error indicates an error that the invoking client or service can fix by modifying the request, requesting permission or by retrying the request. 
- 5xx errror inidicates an issue with lambda or an issue with the function's configuration or resources. 