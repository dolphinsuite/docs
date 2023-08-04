# How to get an SMTP account from Amazon SES?

## What is Amazon SES?

Amazon SES is a cloud email service provider that can integrate into any application for bulk email sending. Whether you use an email software like [SendDolphin](https://senddolphin.com) to send transactional emails, marketing emails, or newsletter emails, you pay only for what you use.

----

## How to get an SMTP account from SES?

Amazon SES is the cheapest email provider out there on the internet. Getting an SMTP account from is not quite simple, fortunately, SES is very friendly to eCommerce business, we are 100% sure that you will manage to do it. Just follow the guide here.

### 1. Get an AWS account

You will be require to sign up for an AWS account if you havenot have it yet. To do so [click here](https://aws.com).

### 2. Config an SNS

Before you are getting to the SES, you will need to config an notification subscription as it is a requirement as long as you use the SES service. Here you go.

* Sign into the [Amazon SNS console](https://console.aws.amazon.com/sns/home) (login with your AWS account)
* On the **Topics page**, choose **Create topic**.
* On the **Create topic** page, in the **Details** section, do the following:
  * For Type, choose **Standard**.
  * Enter a **Name** for the topic, for example `ses-notifications`
  * Enter a **Display name** for the topic, it can be the same as **Name**.



