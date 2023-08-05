[API docs](.) /

# Update or create a contact

## **POST** /restful/api/v3/contact

#### Base URL `https://senddolphin.com`

This endpoint allows you to create a contact if not exists, update otherwise.

You can find all reserved fields and custom fields [here](https://senddolphin.com/my/send-mail/custom-fields). Contact lists can be found or created [here](https://senddolphin.com/my/send-mail/contacts).

### Request body

```json
{
    "email": "example@domain.com",
    "reserved_fields": {
        "last_name": "Stan",
        "first_name": "Lee"
    },
    "custom_fields": {
        "custom_field_1": "Custom value",
        "custom_field_2": "Custom value 2"
    },
    "list_ids":{
        "12345678": 1,
        "23456789": 1
    }
}
```

### Response

```json
{
    "status":true,
    "id":854587151
}
```


