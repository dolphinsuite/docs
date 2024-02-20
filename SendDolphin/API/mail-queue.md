[API docs](.) /

# Queue mails

## **POST** /restful/api/v3/queue

#### Base URL `https://senddolphin.com`

This endpoint allows you to queue and send emails to multiple recipients.

### Attention

1. Activities of mails (like opens and clicks) that sent via this API will not be tracked. If you wish to track the mail activities, you may consider adding your own tracking code to the mail template, or use [Automation](./tutorial-automation) campaigns instead of this API.
2. If `params` is presented in the request body, the `params` data will merge-override to the contact data as the final mail params, and the params will both be applied to the mail subject and mail body. 
3. The queued mails will be sent within minutes in most of cases, however, it may take longer in certain conditions.
4. This API can only queue mails that send to your existing contacts. Any email addresses in the `email_list` list that does not exist in your contact list, or the email address is malformatted, will be omitted.


### Request body

```json
{
    "email_list": ["example@domain.com", "example2@domain.com", "not_exists_in_your_contact_list@domain.com", "malformatted email address"],
    "sender_id": "THE SENDER ID",
    "template_id": "162574473",
    "params": {
        "last_name": "Stan",
        "first_name": "Lee"
    }
}
```

### Response

```json
{
    "status": true,
    "message": "Mail queued.",
    "queued": ["example@domain.com", "example2@domain.com"]
}
```


