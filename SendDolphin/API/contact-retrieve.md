Retrieve a contact

## **GET** /restful/api/v3/contact

#### Base URL `https://senddolphin.com`

This endpoint allows you to retrieve a contact from your account.

### Query string
`email=example@domain.com`

### Response

```json
{
   "status":1,
   "data":{
      "email":"example@domain.com",
      "alternative_emails":"",
      "first_name":"Stan",
      "last_name":"Lee",
      "address_line_1":"",
      "address_line_2":"",
      "city":"",
      "state_province_region":"",
      "postal_code":"",
      "country":"",
      "phone_number":"",
      "whatsapp":"",
      "skype":"",
      "line":"",
      "facebook":"",
      "instagram":"",
      "unique_name":"",
      "custom_field_1":"custom value 1",
      "custom_field_1":"custom value 1"
   },
   "id":"854587151"
}
```