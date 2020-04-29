# aws-serverless-starter
This project provides a comprehensive overview of setting up a project for AWS Serverless development from scratch, following the guide at [Guide: First Serverless Project](https://medium.com/serverlessguru/guide-first-serverless-project-630b91366505).

## What We'll Be Doing

* [__Setup AWS Account__](#setup-aws-account)
  * [Creating an AWS Account](#create-an-aws-account)
  * [Create a Serverless Admin Credential](#create-a-serverless-admin-credential)
  * [Download Access Keys and Secret Access Keys](#download-access-keys-and-secret-aAccess-keys)
* __Installs__
  * installing AWS Command Line Interface (CLI)
  * installing Node Version Manager (`nvm`)
  * installing Node.js (`node`)
  * installing Node Package Manager (`npm`)
  * installing AWS Serverless support (`sls`)
  * Configure the Serverless CLI
* __Setup your Serverless Project__
  * Create the Serverless Project Structure
  * Add Offline & Typescript Support

## Setup AWS Account

### Create an AWS Account
You can signup for your AWS here at [Signup for AWS](https://portal.aws.amazon.com/billing/signup), and simply follow instructions in the link at the top of this README.md file.

### Create a Serverless Admin Credential
AWS strongly recommends separation of privileges when using its cloud services. During AWS Account creation you created a "root user" account. THIS SHOULD NOT BE USED DIRECTLY.

You should instead create additional and alternative user accounts, which is this case will be an account specific to using AWS Serverless, or what we'll call the Serverless Admin account, or credential.

...

### Download Access Keys and Secret Access Keys
...

## Installs

### Installing AWS Command Line Interface (CLI)
Amazon maintains installation packages for the CLI across all major development platforms, so we suggest you drop on by [Installing the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html), to walk you through how to go about doing the install.

### Installing `nvm`
Developing in Node.js means managing its various versions. The absolute BEST way to do that is to use `nvm`. To check if you already have `nvm` installed on your workstation just use:

```bash
command -v nvm
```

`nvm` is a shell function, not a file, so the above command checks to see if `nvm` has been defined in your present login profile. If not, then our advice is to use the [`nvm` Installer](https://github.com/nvm-sh/nvm). Walk through their instructions if you need to install `nvm` on your workstation.

### Installing Node.js (`node`)
With `nvm` now installed and running simply use:
```bash
nvm install 10
```

Verify you are now using the correct version by using:
```bash
node --version
```

Which should result in the result `v10.0.0`.

### Installing `npm`
If you installed Node.js using `nvm` as described above, then `npm` should already be installed for you. You can verify this by using:
```bash
which npm
```

which, for Node.js v10.0.0 would show something such as:
```bash
.../.nvm/versions/node/v10.0.0/bin/npm
```

then verify the version of `npm` you have installed by using:
```bash
npm --version
```

Which for Node.js v10.0.0 will show up as:
```bash
5.6.0
```

### Installing AWS Serverless support
The AWS Serverless package is meant to be used as a command line support tool, so with this `npm` package we'll suggest you install it globally outside your project, so it can be available across your workstation.
```bash
npm install -g serverless
```

### Configure Serverless CLI
Now we will configure the `sls` tool to use the Access and Secret Access Keys we just downloaded.
```bash
serverless config credentials --provider aws --key <Access-Key-ID> --secret <Secret-Access-Key>
```

## Setup the Serverless Project
The main decision you have at this point is whether you wish to build a project using straight JavaScript, or if you prefer to use TypeScript. In this day and age we will likely challenge you on why you WOULDN'T use TypeScript, but we'll leave that up to you to decide (although we will judge you for not using TypeScript).

### Create the Serverless Project structure
```bash
serverless create --path <project-name> --template aws-nodejs-typescript
```

## Offline Support
AWS Serverless allows you to run your AWS Lambda functions locally, so you don't have to deploy them to run them. Here's an example:
```bash
serverless invoke local --function <function-name>
```

### Adding Offline & Typescript Support
```bash
npm install --save-dev serverless-plugin-typescript
npm install --save-dev serverless-dynamodb-local
npm install --save-dev serverless-offline
npm install --save-dev typescript
```

And then add the following to the `serverless.yml`:
```
plugins:
  - serverless-plugin-typescript
  - serverless-dynamodb-local
  - serverless-offline
  ...
```

The order of those lines is IMPORTANT, so keep them in the order shown above.

## Begin Coding Your Project

## Install AWS SDK
Our assumption is that since you've chosen to use AWS Serverless you also intend to use the myriad of AWS services that are available (Lambda, S3, DyanomDB, etc). To install support for those services use the following:
```bash
npm install --save aws-sdk
```

With the above installed add the following line to `handler.ts`:
```javascript
import AWS = 'aws-sdk`
```

# Bibliography
* [NVM Installer on GitHub](https://github.com/nvm-sh/nvm)
* [An Absolute Begginner's Guide to Using `npm`](https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm/)
* [Beginner's Guide to Node.js](https://www.codementor.io/@mercurial/how-to-install-node-js-on-macos-sierra-mphz41ekk)
* [Serverless Plugin Typescript](https://www.serverless.com/plugins/serverless-plugin-typescript/)
* [AWS Serverless Signup](https://www.serverless.com/framework/docs/providers/aws/guide/credentials/)
* [Installing the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
* [Serverless Deployments](https://www.serverless.com/framework/docs/providers/aws/cli-reference/deploy/)

# Other Things to Consider
* [AWS CLI JavaScript Wrapper](https://www.npmjs.com/package/aws-cli-js)
* [Tools for Working with AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-tools.html)
* [AWS Serverless Application Model (SAM)](https://aws.amazon.com/blogs/compute/a-simpler-deployment-experience-with-aws-sam-cli/)
