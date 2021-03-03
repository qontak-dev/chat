# Authentication

In order to use the API, you will need Fulfillment  `Client ID` and `Client Secret`.  `client_id` and `client_secret` used to acquire an access token. An access token grants limited access to a fulfillment service’s account. There are two ways to generate the access token, using HTTP request or using Postman.

- client_id `RRrn6uIxalR_QaHFlcKOqbjHMG63elEdPTair9B9YdY`
- client_secret `Sa8IGIh_HpVK1ZLAF0iFf7jU760osaUNV659pBIZR00` 

## Using HTTP Request to Obtain Access Token

1. Make a POST request to https://chat-service.qontak.com/oauth/token. Example request:

```json http
{
  "method": "POST",
  "url": "https://chat-service.qontak.com/oauth/token",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "username": "<username>",
    "password": "<password>",
    "grant_type": "password",
    "client_id": "RRrn6uIxalR_QaHFlcKOqbjHMG63elEdPTair9B9YdY",
    "client_secret": "Sa8IGIh_HpVK1ZLAF0iFf7jU760osaUNV659pBIZR00"
  }
}
```

2. If successful, you will receive an `access_token` response. When an access token expires, you should request a new token. Example response:

```json
{
  "access_token": "WPuW1u-v21SkfqfC7NNBD9NvNg3ojy8ftuUpVy3ArbU",
  "token_type": "Bearer",
  "expires_in": 29823918,
  "refresh_token": "UU_3xp5jRN0fsNKDrVAEh4QqdRody3Wc37VQHFZ37C4",
  "created_at": 1594354514
}
```

3. You can use the access_token to make HTTP request, for example:

```bash
curl --request GET \
  --url https://chat-service.qontak.com/api/open/v1/health \
  --header 'Authorization: Bearer ${ACCESS_TOKEN}'
```

## Using Postman

Postman is an application that lets you send HTTP requests to  API endpoints. You can use Postman to obtain `access_token`. Here are the complete steps:

1. Open Postman. Visit [Get Postman](https://www.getpostman.com/downloads/) to download.
2. Click the Authorization tab under the request URL and select OAuth 2.0 as the Type
3. Click on the Get New Access Token
4. Select `Password` as the Grant Type
5. Input https://chat-service.qontak.com/oauth/token to the Access Token URL field
6. Enter your Client ID and Client Secret
7. Finally, click on the Request Token button.




