[API](.) /

# Add a contact to lists

## **PUT** /restful/api/v3/contact

#### Base URL `https://senddolphin.com`

This endpoint allows you to create add/remove a contact from a contact list.

Contact lists can be found or create [here](https://senddolphin.com/my/send-mail/contacts).

### Request body

```json
{
    "email": "example@domain.com",
    "list_ids":{
        "12345678": 1,
        "23456789": 1
    }
}
```

Explanation:
```
"list_ids":{
    "12345678": 1, # Adding the contact to list "12345678"
    "23456789": 0  # Removing the contact from list "12345678"
}
```


### Response

```json
{
    "status":true,
    "id":854587151
}
```


