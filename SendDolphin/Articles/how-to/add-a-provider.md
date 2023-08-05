[Articles](../) \ [How-to](.) \

# Adding a provider

You may add one or more mailing providers support SMTP Relay like SES (by AWS) and SendGrid that allow the senders to send out mass emails. Here are the providers we support now.

* Amazon SES [Get an Amazon SES SMTP credentials](get-ses-smtp-credentials)
* SendGrid [Get a SendGrid SMTP credentials](./get-sendgrid-smtp-credentials)
* Generic SMTP services support TLS.
* SendDolphin built-in provider (is already built-in in your acocunt, need manual adding required)

## Add a mailing provider to your SendDolphin account

After getting your SMTP credentials ready, you shall proceed adding a provider on your SendDolphin account.

* Login to your [SendDolphin](https://senddolphin.com) account.
* Choose **Provider** in the left navigation.
* Choose **Create Provider** at the right-top corner.
* On the **Create Provider** page, do following
  * For **Provider**, choose the respective platform. If the platform is not in the dropdown list, choose **Generic SMTP**
  * For **Host**, enter the SMTP endpoint (or SMTP server host) you have got from the provider.
  * For **Username** and **Password**, enter your SMTP credentials. `For SendGrid, use "apikey" as the username. This setting is the exact string "apikey" and not the API key itself. And use the API key itself as the password.`
* Choose **Save Provider**.


## Related articles
* [Add a sender](./add-a-sender)

