[API](.) /

# Delete a contact

## **DELETE** /restful/api/v3/contact

#### Base URL `https://senddolphin.com`

This endpoint allows you to delete contact from your account.

### Request body

```json
{
    "email": "example@domain.com",
}
```

### Response

```json
{
    "status":true
}
```

### Important

All queued mails associated to the contact will also be deleted.

