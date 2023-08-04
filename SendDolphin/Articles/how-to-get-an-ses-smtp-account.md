# How to get an SMTP account from Amazon SES?

## What is Amazon SES?

Amazon SES is the cheapest email provider out there on the internet that can integrate into any application for bulk email sending. Whether you use an email software like [SendDolphin](https://senddolphin.com) to send transactional emails, marketing emails, or newsletter emails, you pay only for what you use. Just follow the guide here to get your SMTP details.

## 1. Get an AWS account

You will be require to sign up for an AWS account if you havenot have it yet. To do so [click here](https://aws.com).

## 2. Config an SNS

Before you are getting to the SES, you will need to config an notification subscription as it is a requirement as long as you use the SES service. Here you go.

* Sign into the [Amazon SNS console](https://console.aws.amazon.com/sns/home) (login with your AWS account)
* On the **Topics page**, choose **Create topic**.
* On the **Create topic** page, in the **Details** section, do the following:
  * For **Type**, choose **Standard**.
  * Enter a **Name** for the topic, for example `ses-notifications`
  * Enter a **Display name** for the topic, it can be the same as **Name**.
  * Choose **Create topic** at the bottom of the page. Then the topic will be created and the **topic page** will be displayed.
* On the **topic page**, you will continue to create a subscription for the topic. To do so choose **Create subscription** on the **Subscriptions** section.
* On the **Create subscription** page, in **Details** section, do the following:
  * For **Topic ARN**, choose the the topic you have just created. It should look like `arn:aws:sns:us-east-2:123456789012:the-topic-name`.
  * For **Protocol**, choose **HTTPS**.
  * For **Endpoint**, enter your SES notification handler which you can find [here](https://senddolphin.com/my/send-mail/http-handlers).
  * Choose **Create subscription** at the bottom of the page.
* You have done the SNS configuration.

## 3. Setup your SES

You have just done configurating the SNS. Now you may proceed setting up your SES.

* Sign into the [Amazon SES console](https://console.aws.amazon.com/ses/) (login with your AWS account)
* In the navigation pane, under **Configuration**, choose **Verified identities**.
* Choose **Create identity**.
* Under **Identity details**, select **Domain** as the type of identity you want to create. You must have access to the domain’s DNS settings to complete the domain verification process.
* Enter the name of the domain or subdomain in the **Domain** field. `
If your domain is www.example.com, enter example.com as your domain. Don't include the "www." part, because the domain verification process won't succeed if you do.
`
* Under **Verifying your domain**, choose **Advanced DKIM settings** and do following:
  * For **Identity type**, choose **Easy DKIM**.
  * For **DKIM signing key length**, choose **RSA_2048_BIT**.
  * Ensure that the **Enabled** box is checked in the **DKIM signatures** field.
* Choose **Create idntity** at the bottom of the page.

### Verifying a DKIM domain identity with your DNS provider

After you’ve created your domain identity configured with DKIM, you must complete the verification process with your DNS provider by following procedures.

* From the Publish DNS records table, copy the three CNAME records that appear in this section to be published (added) to your DNS provider. Alternatively, you can choose Download .csv record set to save a copy of the records to your computer.
* The following image shows an example of the CNAME records to publish to your DNS provider. ![Example of the CNAME records to publish to your DNS provider](https://docs.aws.amazon.com/images/ses/latest/dg/images/dkim_records.png "Example of the CNAME records to publish to your DNS provider")
* Login to your domain’s DNS or web hosting provider, and then add the CNAME records containing the values that you copied or saved previously. For more details see the [DNS/Hosting provider table](https://docs.aws.amazon.com/ses/latest/dg/creating-identities.html#just-verify-domain-proc) following these procedures.


