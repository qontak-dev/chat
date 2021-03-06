## Introduction

This document contains the reference and guideline for Chat API Services. This API allows you to integrate your app into Qontak. You can manage outbound message, incoming message, and chat rooms using all API’s that we provided on this document. Qontak API Services is a JSON-based OAuth2 API. All requests must be secure (https) and [authenticated](../Guide/Authentication.md).

## Basic API usage
All the requests referenced in the documentation start with https://chat-service.qontak.com.

## Authentication

Each API request requires authentication to identify the permission that is responsible for making the request. Authentication is provided by access tokens.

### Where are my access tokens?
- `User access token` - allows you to send whatsapp hsm template. This is a private usage token and should never be shared as it gives full access to your account.
- `Bot token` - allows only bot endpoint requests for Chatbot interaction.

### Authentication example

Include this HTTP header for each API request:

```Authorization: Bearer ${ACCESS_TOKEN}```

Example request


```bash
curl --request GET \
  --url https://chat-service.qontak.com/api/open/v1/health \
  --header 'Authorization: Bearer ${ACCESS_TOKEN}'
```



## Featured API
- [Webhooks API](Webhook.md): Register webhook to get notification through your system.
- [WhatsApp Outbound API](WhatsApp-API.md): Send WhatsApp outbound template message to your customer.
- [Message API](Send-Message.md): Send message to your customer within session window.

## Use Case

Token | Usecase
------- | -------
User | Create and send outbound message templates 
Bot | Create Chatbot using Webhooks Message Interaction
