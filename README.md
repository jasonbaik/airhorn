![Airhorn Logo](docs/images/logo-horizontal.png "Airhorn Logo")

-----

[![build](https://github.com/jaredwray/airhorn/actions/workflows/build.yaml/badge.svg)](https://github.com/jaredwray/airhorn/actions/workflows/build.yaml)
[![release](https://github.com/jaredwray/airhorn/actions/workflows/release.yaml/badge.svg)](https://github.com/jaredwray/airhorn/actions/workflows/release.yaml)
[![codecov](https://codecov.io/gh/jaredwray/airhorn/branch/main/graph/badge.svg?token=4OJEEB67Q5)](https://codecov.io/gh/jaredwray/airhorn)
[![license](https://img.shields.io/github/license/jaredwray/airhorn)](https://github.com/jaredwray/airhorn/blob/master/LICENSE)
[![npm](https://img.shields.io/npm/dm/airhorn)](https://npmjs.com/package/airhorn)

## Cloud Native Notifications Library

Airhorn is built to enable a more robust notification system. We focused on making it cloud native by default (using cloud services).

## Features

* GitOps Based Templating System - email, sms, mobile push, and webhooks all in one place!
* Email Notifications - easily send email across multple providers and even load balance or active/passive fail over. 
* SMS Notifications - SMS that is easy to use via a robust template system. 
* Mobile Push Notifications - Push to IOS and Android devices.
* Webhook Notifications - Built right into the system as a native feature with retry support.
* 100% Code Coverage / Tested with Integration Tests
* Built using ecto for handling multiple templates

# Settings / Opts

templatePath
defaultTemplateLanguage
...

## Cloud Services
* Email: Twilio Sendgrid and AWS SES
* SMS: Twilio and AWS SNS
* Mobile Push: Google Firebase and AWS SNS

## Library API

- Templates
- Providers
- send()

## Examples on how to use
- sending a simple email

```javascript
const airhorn = require('airhorn');
await airhorn.send('john@doe.org', 'hello@testing.com', 'generic-template-foo', ProviderType.SMTP);
```

- sending a simple webhook
- using two email providers
- creating a template and sending it
- how the template forlder structure works
- how template overrides work `subject` in the template

## How to setup Firebase for Mobile Push

To implement Firebase in your application, you will need to create a new project in the Firebase console and integrate
the Firebase SDK according to the [Firebase documentation](https://firebase.google.com/docs/cloud-messaging).

In your Firebase Project Settings, go to the `Service accounts` tab to generate your `private key` as a json file and 
put the content of the file as `FIREBASE_CERT` environment variable.

## How to setup AWS SNS for Mobile Push

To implement AWS SNS you will need to create a new SNS application in the AWS console and integrate the AWS SNS SDK in 
your application. 

### User notification overview 

1. [Obtain the credentials and device token](https://docs.aws.amazon.com/sns/latest/dg/sns-prerequisites-for-mobile-push-notifications.html) for the mobile platforms that you want to support.
2. Use the credentials to create a platform application object (PlatformApplicationArn) using Amazon SNS. For more information, see [Creating a platform endpoint](https://docs.aws.amazon.com/sns/latest/dg/mobile-platform-endpoint.html). 
3. Use the returned credentials to request a device token for your mobile app and device from the mobile platforms. The token you receive represents your mobile app and device.
4. Use the device token and the PlatformApplicationArn to create a platform endpoint object (EndpointArn) using Amazon SNS. For more information, see [Creating a platform endpoint](https://docs.aws.amazon.com/sns/latest/dg/mobile-platform-endpoint.html).
5. Send the push message to the device endpoint (EndpointArn) using `airhorn`. 

```javascript
const airhorn = require('airhorn');
await airhorn.send('endpointArn', '', 'generic-template-foo', ProviderType.MOBILE_PUSH);
```

---- 

## How to Contribute 



