# aws-serverless-starter
This project provides a comprehensive overview of setting up a project for AWS Serverless development from scratch, following the guide at [Guide: First Serverless Project](https://medium.com/serverlessguru/guide-first-serverless-project-630b91366505).

## What We'll Be Doing
* installing Node Version Manager (`nvm`)
* installing Node Package Manager (`npm`)
* installing AWS Serverless tools (`sls`)
* Creating an AWS Account
* Creating an AWS User Credential to act as an admin for Serverless operations
* Downloading AWS Access Key ID and Secret Access Key for that admin user

## Installs

### Installing `nvm`
...

### Installing `npm`
...

### Installing AWS Serverless
The AWS Serverless package is meant to be used as a command line support tool, so with this `npm` package we'll suggest you install it globally outside your project, so it can be available across your workstation.
```
npm install -g serverless
```

## Setup AWS Account

### Creating an AWS Account
You can signup for your AWS here at [Signup for AWS](https://portal.aws.amazon.com/billing/signup), and simply follow instructions in the link at the top of this README.md file.

### Creating a Serverless Admin Credential
...

### Downloading Access Keys and Secret Access Keys
...

### Configuring Serverless CLI
Now we will configure the `sls` tool to use the Access and Secret Access Keys we just downloaded.
```
serverless config credentials --provider aws --key <Access-Key-ID> --secret <Secret-Access-Key>
```
