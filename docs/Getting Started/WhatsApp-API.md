# Whatsapp API


Who Can Use This Feature |
--------- |
`User Token`  |
All plans with `WhatsApp Channel` | 



Get started send WhatsApp messages template to customer.


## Set Up
Before Start using The API please make sure you have already prepare your :
- [WhatsApp Business Account](https://docs.qontak.com/docs/hub/docs/Overview.md#business-account) and set up a line of credit, you can get [here](https://docs.qontak.com/docs/hub/docs/Overview.md#business-solution-providers).
- [WhatsApp Business API Server](https://docs.qontak.com/docs/hub/docs/Others/Glossary.md#whatsapp-business-api-server), you can ask your [BSP](https://docs.qontak.com/docs/hub/docs/Others/Glossary.md#business-solution-providers).
- Verified WhatsApp Business Phone Number.
- [Qontak Hub Account](https://docs.qontak.com/docs/hub/docs/Others/Glossary.md#qontak-hub-account), you can get [here](https://docs.qontak.com/docs/hub/docs/Others/Glossary.md#qontak-hub-account).
## Authentication

For testing our API you can use your production account directlyt:


Production:
    https://chat-service.qontak.com/oauth/token
  - client_id `RRrn6uIxalR_QaHFlcKOqbjHMG63elEdPTair9B9YdY`
  - cleint_secret `Sa8IGIh_HpVK1ZLAF0iFf7jU760osaUNV659pBIZR00` 



Please change your JSON body request using your  [Qontak Hub Account](https://docs.qontak.com/docs/hub/docs/Others/Glossary.md#qontak-hub-account) credentials:
```json
{
  "username": "<username>",
  "password": "<password>",
  "grant_type": "password",
  "client_id": "<client_id>",
  "client_secret": "<client_secret>"
}
```
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
    "client_id": "<client_id>",
    "client_secret": "<client_secret>"
  }
}
```

Response example

```json
{
  "access_token": "WPuW1u-v21SkfqfC7NNBD9NvNg3ojy8ftuUpVy3ArbU",
  "token_type": "Bearer",
  "expires_in": 29823918,
  "refresh_token": "UU_3xp5jRN0fsNKDrVAEh4QqdRody3Wc37VQHFZ37C4",
  "created_at": 1594354514
}
```
## Setup WhatsApp Channel
We need to setup WhatsApp Channel Integration before send message using [WhatsApp Business API Server](https://docs.qontak.com/docs/hub/docs/Others/Glossary.md#whatsapp-business-api-server).
### Get available WhatsApp channels.
```json http
{
  "method": "get",
  "url": "https://chat-service.qontak.com/api/open/v1/integrations",
  "query": {
    "target_channel": "wa"
  },
  "headers": {
    "Authorization": "Bearer {{access_token}}"
  }
}
```
Response
```json
{
  "status": "success",
  "data": [
    {
      "id": "c3370195-3451-4645-99a1-578c47b24d41",
      "target_channel": "wa",
      "webhook": "LswudlTUZRpJErf-kqHB2A",
      "settings": {
        "domain_server": "https://api-whatsapp.qontak.net",
        "authorization": "Y7Rt3W43VGVyhmFuZzgyM4E=",
        "account_name": "Qontak",
        "server_wa_id": "6288233262100"
      },
      "organization_id": "7e6e0187-6707-464f-8b99-59b094caae0b",
      "created_at": "2020-07-28T02:43:30.060+00:00"
    }
  ],
  "meta": {
    "pagination": {
      "cursor": {
        "next": "MTU5NTUwOTI3Ny4yNDY=",
        "prev": "MTU5NTkwNDIxMC4wNg=="
      },
      "offset": 1,
      "limit": 4,
      "total": 4
    }
  }
}
```
### Channel Integration ID
Here available Channel Integration ID `string:uuid` from response above.
- **channel_integration_id**: `c3370195-3451-4645-99a1-578c47b24d41`
### Common Channel Integration Use Cases :
- [Connect to Channel WhatsApp Business API Server](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1integrations~1wa/post).
- [Connect to Channel Qontak CRM](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1integrations~1qontak/post)
- [Connect to Channel Qiscus](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1integrations~1direct_qiscus/post)
- [Disconnect Cannel](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1integrations~1%7Bid%7D/delete)
## Setup WhatsApp message templates
We need to have approved WhatsApp message templates before send Notification Message.
### Get available WhatsApp message template
```json http
{
  "method": "get",
  "url": "https://chat-service.qontak.com/api/open/v1/templates/whatsapp",
  "headers": {
    "Authorization": "Bearer {{access_token}}"
  }
}
```
Example Response
```json
{
  "status": "success",
  "data": [
    {
      "id": "cf7a16bd-e84f-4f72-8cce-70934edfc585",
      "name": "message",
      "language": "id",
      "header": null,
      "body": "Hi {{1}}, Silakan periksa invoice di email anda.",
      "footer": null,
      "status": "APPROVED",
      "category": "PAYMENT_UPDATE"
    }
  ],
  "meta": {
    "pagination": {
      "cursor": {
        "next": "MTU5MTI1OTg5OC45NzQwMDAy",
        "prev": "MTU5NTkwODgwNy4yNjQ5OTk5"
      },
      "offset": 1,
      "limit": 48,
      "total": 48
    }
  }
}
```
### WhatsApp Message Template ID
Here available WhatsApp Message Template ID `string:uuid` from response above.
- **message_template_id**: `cf7a16bd-e84f-4f72-8cce-70934edfc585`
### Common WhatsApp Template Use Cases :
- [List available category WhatsApp Template](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1templates~1category/get)
- [List available language for WhatsApp Template](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1templates~1language/get)
- [Create WhatsApp Template](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1templates~1whatsapp/post)
- [List WhatsApp Template](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1templates~1whatsapp/get)
- [Detail WhatsApp Template](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1templates~1%7Bid%7D~1whatsapp/get)
- [Delete WhatsApp Template](https://docs.qontak.com/docs/hub/swagger/openapi.yaml/paths/~1v1~1templates~1whatsapp/delete)
## Create and send message templates
Required parameters to send WhatsApp message templates :
- Valid WhatsApp Phone Number
- [message_template_id](https://docs.qontak.com/docs/hub/docs/Get-Started/Get-Started.md#whatsapp-message-template-id)
- [channel_integration_id](https://docs.qontak.com/docs/hub/docs/Get-Started/Get-Started.md#channel-integration-id)
```json http
{
  "method": "POST",
  "url": "https://chat-service.qontak.com/api/open/v1/broadcasts/whatsapp/direct",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Bearer {{access_token}}"
  },
  "body": {
    "to_number": "628117661000",
    "to_name": "Burhanudin Hakim",
    "message_template_id": "cf7a16bd-e84f-4f72-8cce-70934edfc585",
    "channel_integration_id": "c3370195-3451-4645-99a1-578c47b24d41",
    "language": {
      "code": "id"
    },
    "parameters": {
      "body": [
        {
          "key": "1",
          "value": "full_name",
          "value_text": "Burhanudin Hakim"
        }
      ]
    }
  }
}
```
Example Results
```json
{
  "status": "success",
  "data": {
    "id": "6d38b2cf-84a7-406c-9bd3-8c8c59787e8b",
    "name": "Burhanudin Hakim",
    "organization_id": "7e6e0187-6707-464f-8b99-59b094caae0b",
    "channel_integration_id": "c3370195-3451-4645-99a1-578c47b24d41",
    "contact_list_id": null,
    "contact_id": "a803020b-81f6-46bc-ad34-2dd7c871dd57",
    "target_channel": "wa",
    "parameters": {
      "header": {},
      "body": {
        "1": "full_name"
      }
    },
    "created_at": "2020-07-30T07:24:13.040Z",
    "message_status_count": {
      "failed": 0,
      "delivered": 0,
      "read": 0,
      "pending": 0,
      "sent": 0
    },
    "message_template": {
      "id": "cf7a16bd-e84f-4f72-8cce-70934edfc585",
      "name": "message",
      "language": "id",
      "header": null,
      "body": "Hi {{1}}, Silakan periksa invoice di email anda.",
      "footer": null,
      "status": "APPROVED",
      "category": "PAYMENT_UPDATE"
    }
  }
}
```
#### Next Steps
Get Detail [API Reference](https://docs.qontak.com/docs/hub/swagger/openapi.yaml) to get full spesification of the API or [Public Qontak Hub API](https://app.swaggerhub.com/apis-docs/qontak-dev/hub/) page.
