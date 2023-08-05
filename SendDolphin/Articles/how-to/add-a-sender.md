[Articles](../) \ [How-to](.) \

# Adding a sender

A Sender is an identity that represents your “From” email address — the address your recipients will see as the sender of your emails.

Senders you have added or adding to the Senders section, must be verified on (or allowed by) the mailing-provider's platform, otherwise it may not be able to send mails.

To add a sender to your SendDolphin account, follow the respective instructures.

## Use SendDolphin provider

* In your SendDolphin account, choose **Senders** in the left navigation.
* Choose **Add sender** at the right-top corner.
* On the **Add sender** page, do following
  * For **Provider**, choose **SendDolphin**.
  * For **Sender name**, choose a name that represents your business, the name your recipients will see as the sender of your emails. 
  * For **Sender address**, the address is fixed, it looks like `sds.12345678@senddolphin.net`.
  * For **Reply to email**, choose an email address that your would like to receive the mail replies to, it can be any email address, that is different from **Sender address**. In the example below, `sds.12345678@senddolphin.net` is the **Sender address** `service@gmail.com` is the **Reply to email**, when a recipient clicks Reply on the email you send out via this sender, the reply message is sent to `service@gmail.com` instead of `sds.12345678@senddolphin.net`.
* Choose **Save Sender**.


## Use custom provider

* In your SendDolphin account, choose **Senders** in the left navigation.
* Choose **Add sender** at the right-top corner.
* On the **Add sender** page, do following
  * For **Provider**, choose the respective provider which you have added on the **Providers** page before.
  * For **Sender name**, choose a name that represents your business, the name your recipients will see as the sender of your emails. 
  * For **Sender address**, enter an email address that you are going to use as your “From” address while sending emails. The postfix of **Sender email** must match a domian that you have got it verified on the prvoider platform. For example, you have a **Verified Identity** with domian `sampledomain.com` on Amazon SES, you may use `some-prefix@sampledomain.com` as the **Sender email**.
  * For **Reply to email**, choose an email address that your would like to receive the mail replies to, it can be any email address, that is different from **Sender address**. In the example below, `marketing@sampledomain.com` is the **Sender address** `service@gmail.com` is the **Reply to email**, when a recipient clicks Reply on the email you send out via this sender, the reply message is sent to `service@gmail.com` instead of `marketing@sampledomain.com`.
* Choose **Save Sender**.


## Related articles
* [Add a provider](./add-a-provider)