[API docs](.) /

# Send an Email

## **POST** /restful/api/v3/mail

#### Base URL `https://senddolphin.com`

This endpoint allows you to send an email to a specific address.

### Attention

1. Activities of mails (like opens and clicks) that sent via this API will not be tracked. If you wish to track the mail activities, you may consider adding your own tracking code to the mail body, or use [Automation](./tutorial-automation) campaigns instead of this API.
2. If the recipient address is an existing contact in your list and `params` is set in the API request body, the `params` data will merge-override to the contact data as the final mail params, and the params will both be applied to the mail subject and mail body. 
3. If you have set `template_id` to the request body, then `subject` and `body` should not be included.
4. This is a single mail sender, and mail will be sent immediately once you make the call. If you wish to send bulk mail, please use the [Queue](./mail-queue) API.


### Request body

**Send with template**
```json
{
    "email": "example@domain.com",
    "sender_id": "THE SENDER ID",
    "template_id": "THEM TEMPLATE ID",
    "params": {
        "last_name": "Stan",
        "first_name": "Lee"
    }
}
```

**Send with custom subject and body**
```json
{
    "email": "example@domain.com",
    "sender_id": "THE SENDER ID",
    "subject": "Mail subject here",
    "body": "This is the mail body.",
    "params": {
        "last_name": "Stan",
        "first_name": "Lee"
    },
    "is_html": false
}
```

```
is_html: set `true` if the body is HTML content.
```

### Response

```json
{
    "status": true,
    "message": "Mail sent."
}
```


