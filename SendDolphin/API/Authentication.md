To authenticate, add an `Authorization` header to your API request that contains your [API Key](https://senddolphin.com/my/send-mail/api).

## Example Header

```bash
curl \
  -H "Authorization: Bearer Your.API.Key-HERE" \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{"email": "example@domian.com"}' \
  https://senddolphin.com/restful/api/v3/contact
```