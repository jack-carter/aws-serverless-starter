# aws-serverless-starter
This project provides a comprehensive overview of setting up a project for AWS Serverless development from scratch, following the guide at [Guide: First Serverless Project](https://medium.com/serverlessguru/guide-first-serverless-project-630b91366505).

## What We'll Be Doing
* installing Node Version Manager (`nvm`)
* installing Node.js version 10
* installing Node Package Manager (`npm`)
* installing AWS Serverless tools (`sls`)
* Creating an AWS Account
* Creating an AWS User Credential to act as an admin for Serverless operations
* Downloading AWS Access Key ID and Secret Access Key for that admin user

## Installs

### Installing `nvm`
Developing in Node.js means managing its various versions. The absolute BEST way to do that is to use `nvm`. To check if you already have `nvm` installed on your workstation just use:

```bash
command -v nvm
```

`nvm` is a shell function, not a file, so the above command checks to see if `nvm` has been defined in your present login profile. If not, then our advice is to use the [`nvm` Installer](https://github.com/nvm-sh/nvm). Walk through their instructions if you need to install `nvm` on your workstation.

### Installing Node.js
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

## Setup AWS Account

### Create an AWS Account
You can signup for your AWS here at [Signup for AWS](https://portal.aws.amazon.com/billing/signup), and simply follow instructions in the link at the top of this README.md file.

### Create a Serverless Admin Credential
AWS strongly recommends separation of privileges when using its cloud services. During AWS Account creation you created a "root user" account. THIS SHOULD NOT BE USED DIRECTLY.

You should instead create additional and alternative user accounts, which is this case will be an account specific to using AWS Serverless, or what we'll call the Serverless Admin account, or credential.

...

### Download Access Keys and Secret Access Keys
...

### Configure Serverless CLI
Now we will configure the `sls` tool to use the Access and Secret Access Keys we just downloaded.
```bash
serverless config credentials --provider aws --key <Access-Key-ID> --secret <Secret-Access-Key>
```

## Structure the Serverless Project
The main decision you have at this point is whether you wish to build a project using straight JavaScript, or if you prefer to use TypeScript. In this day and age we will likely challenge you on why you WOULDN'T use TypeScript, but we'll leave that up to you to decide (although we will judge you for not using TypeScript).

### Create the Serverless Project structure
```bash
serverless create --path <project-name> --template aws-nodes-typescript
```

## Offline Support
AWS Serverless allows you to run your AWS Lambda functions locally, so you don't have to deploy them to run them.

### Adding Offline Typescript Support
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

# Bibliography
* [NVM Installer on GitHub](https://github.com/nvm-sh/nvm)
* [Beginner's Guide to Node.js](https://www.codementor.io/@mercurial/how-to-install-node-js-on-macos-sierra-mphz41ekk)
* [Serverless Plugin Typescript](https://www.serverless.com/plugins/serverless-plugin-typescript/)
* [An Absolute Begginner's Guide to Using `npm`](https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm/)
