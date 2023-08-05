[Articles](../) \ [How-to](.) \

# How to get an SMTP credentials from Amazon SES?

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
  * For **Endpoint**, enter `https://senddolphin.com/send-mail/public/ses-notification-handler?subscription-id={YOUR-ACCOUNT-ID}`. You can find your account ID [here](https://senddolphin.com/account/profile).
  * Choose **Create subscription** at the bottom of the page.
* You have done the SNS configuration.

## 3. Setup your SES

You have just done configurating the SNS. Now you may proceed setting up your SES.

### Create a domian identity

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

### Setting up event notification for SES

In order to send email using Amazon SES, you must setup the event notification for managing bounces and complaints.

* In the navigation pane, under **Configuration**, choose **Verified identities**.
* In the **Identities** container, select the verified identity you have just created.
* In the details screen of the verified identity you selected, choose the **Notifications** tab and select **Edit** in the **Feedback notifications** container.
* For **Bounce feedback**, **Complaint feedback** and **Delivery feedback** choose the SNS topic you have created at the beginning.
* Choose **Save changes**

### Obtaining SES SMTP credentials

You need SES SMTP credentials to add a provider on [SendDolphin](https://senddolphin.com/my/send-mail/providers), so SendDolphin be able to send email through the SES for you account.

* Choose **SMTP settings** in the left navigation pane - this will open the Simple Mail Transfer Protocol (SMTP) settings page.
* On the page, under **Simple Mail Transfer Protocol (SMTP) settings**, find the **SMTP endpoint**. It should look like `email-smtp.us-east-1.amazonaws.com`.
* Choose **Create SMTP credentials** in the upper-right corner - the IAM console will open.
* For **Create User for SMTP**, type a name for your SMTP user in the **User Name** field. Alternatively, you can use the default value that is provided in this field. When you finish, choose **Create user** in the bottom-right corner.
* Expand **Show** under SMTP password - your SMTP credentials are shown on the screen.
Download these credentials by choosing **Download .csv** file or copy them and store them in a safe place, because you can't view or save your credentials after you close this dialog box.
* Choose **Return to SES console**.

### Add a provider on SendDolphin

After getting your SES SMTP credentials ready, you shall proceed to add a provider on your SendDolphin account. To do so:

* Login to your [SendDolphin](https://senddolphin.com) account.
* Choose **Provider** in the left navigation.
* Choose **Create Provider** at the right-top corner.
* For **Provider**, choose AWS SES.
* For **Host**, enter the SES SMTP endpoint.
* For **Username** and **Password**, enter your SES SMTP credentials.
* Choose **Save Provider**.

### Add a sender on SendDolphin

* In your SendDolphin account, choose **Senders** in the left navigation.
* Choose **Add sender** at the right-top corner.
* On the **Add sender** page, do following
  * For **Provider**, choose the provider you have just added.
  * For **Sender name**, choose a name that represents your business, the name your recipients will see as the sender of your emails. 
  * For **Sender address**, choose an email address that you are going to use as your “From” address while sending emails. The postfix of **Sender email** must match a domian of **Verified Idenities** on your SES console. For example, you have a **Verified Identity** with domian `sampledomain.com`, you may use `xxx@sampledomain.com` as the **Sender email**.
  * For **Reply to email**, choose an email address that your would like to receive the mail replies to, it can be any email address, that is different from **Sender address**. In the example below, `marketing@sampledomain.com` is the **Sender address** `service@gmail.com` is the **Reply to email**, when a recipient clicks Reply on the email you send out via this sender, the reply message is sent to `service@gmail.com` instead of `marketing@sampledomain.com`.
* Choose **Save Sender**.
* Go back to the SES console.

### Request SES production access

Now you have done all things needed to get your SES credentials. The last thing is to move out of from the Amazon SES sandbox.

* on the Amazon SES console, in the navigation pane, choose **Account dashboard**.
* In the warning box at the top of the console that says, "Your Amazon SES account is in the sandbox", on the right-hand side, choose **Request production access**.
* In the account details modal, select either the **Marketing** or **Transactional** radio button that best describes the majority of mail you'll be sending.
   * **Marketing email** - Sent on a one-to-many basis to a targeted list of prospects or customers containing marketing and promotional content such as to make a purchase, download information, etc.
   * **Transactional email** - Sent on a one-to-one basis unique to each recipient usually triggered by a user action such as a website purchase, a password reset request, etc.
* In **Use case description**, explain how you plan to use Amazon SES to send email. You should answer the following questions:
  * How do you plan to build or acquire your mailing list?
  * How do you plan to handle bounces and complaints?
  * How can recipients opt out of receiving email from you?
  * How did you choose the sending rate or sending quota that you specified in this request?
* You will also need to prepare 3 email templates which you are sending or plan to send to your audience. You can create template on your SendDolphin account. To do so [click here](https://senddolphin.com/my/send-mail/templates).

Here are the some examples of Q&A for requesting SES production access.

```
Q: How do you plan to build or acquire your mailing list? 
A: We have an website, when a user signs up to our website or newsletters, we will add his/her email to our mailing list.
```

```
Q: How you maintain your recipient lists?
A: When the user's account is  deleted, suspended or deactivated, the user's email will be removed from our mailing list promptly and automatically.
```

```
Q: How do you manage bounces, complaints?
A: We are subscribing to the SES notifications. When a bounce or complaint event received, we will remove the email address from our mailing list promptly and automatically.
```

```
Q: How do you maintain unsubscribe requests?
A: There is an "unsubscribe" link on the emails we sent out. When someone click on it, the recipient's email address will be removed from our mailing list promptly and automatically. Our users are also able to opt out from the mailing list in thier accounts.
```

That's all. Once you submit a review of your account details, you can’t edit your details until the review is complete. The AWS Support team provides an initial response to your request within 24 hours.
