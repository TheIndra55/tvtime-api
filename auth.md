# Authentication

For endpoints that require to be logged in `TVST_ACCESS_TOKEN` header is used, you can get an access token by using the login endpoint. 

## Login

Logs in using a username and password

```
POST /signin
```

Body:
| Name | Type | Description |
|------|------|-------------|
| username | string | The username of the account |
| passsword | string | The password of the account |

The body needs to be content type `multipart/form-data` or `application/x-www-form-urlencoded`.

Response:
```json
{
    "result": "OK",
    "id": "44823385",
    "tvst_access_token": "..."
    [...]
}
```

tvst_access_token will be your access token to access endpoints that require authentication.