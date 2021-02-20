# Overview

Now businesses can use WhatsApp Business API to connect with their customers.  The WhatsApp Business API client supports a subset of the features provided by the WhatsApp applications you already know from Android, iOS, and the web, including end-to-end encryption. The difference is that this application can be **deployed on a server**, **providing a local API** that allows you to programmatically send and receive messages and integrate this workflow with your own systems

## Resources

### Business Solution Providers
If you are looking to get started with the WhatsApp Business API right away, Qontak.com is a business solution providers (BSP) that can help you with setup and integration. Please contact admin@qontak.com to register a WhatsApp Business Account.

## How It Works
### Business Account
The first step for businesses to communicate with customers on WhatsApp is to create a WhatsApp business account and set up a line of credit. This business account will allow people to easily identify your business and find out more information such as your address, hours of operation, website, and description. Through your account in the Facebook Business Manager you will have the ability to create message templates for sending notifications to customers at scale.

### Messaging

**WhatsApp message templates** and media message templates are specific message formats that businesses use to send out notifications or customer care messages to people that have opted in to notifications. Messages can include appointment reminders, shipping information, issue resolution and payment updates. These are the preferred method of reaching customers.

Other types of messages such as text and media, must be sent within a **24-hour window of a message from a customer**.


### How WhatsApp Business API Works


#### Inbound Message

![WhatsApp Business API Server](https://raw.githubusercontent.com/qontak-dev/docs/master/images/wa-business-api-server.png "WhatsApp Business API Server")


1. A Customer send message to WhatsApp Business Number.
2. WhatsApp send message to WhatsApp Business API Server.
3. The WhatsApp Business API Server send **webhooks** to http endpoint triggered by :
    - [Inbound Message Notifications](https://developers.facebook.com/docs/whatsapp/api/webhooks/inbound)
    - [Inbound Media Message Notifications](https://developers.facebook.com/docs/whatsapp/api/webhooks/inbound#mediawebhook)
    - [Inbound Replies to Sent Messages](https://developers.facebook.com/docs/whatsapp/api/webhooks/inbound#context)
    - [Inbound System Messages](https://developers.facebook.com/docs/whatsapp/api/webhooks/inbound#system)
    - [Outbound Message Status Notifications](https://developers.facebook.com/docs/whatsapp/api/webhooks/outbound)
4. The Application register webhook endpoint to receive the data
5. The Application send message  using API

> *Webhooks are user-defined HTTP callbacks that are triggered by specific events*




#### Outbound Message

![Notification Message](https://raw.githubusercontent.com/qontak-dev/docs/master/images/wa-business-api-outbound-message.png)

There are two types of outbound messages: Notification Message and Customer Service Message.

- The **Customer Service Message** only available in the **24-hour window from last customer message**.
- The **Notification Message** can only send WhatsApp message templates only.


##### Notification Message

![Notification Message](https://raw.githubusercontent.com/qontak-dev/docs/master/images/wa-business-api-outbound.png)
1. The Application create [WhatsApp message templates](https://docs.qontak.com/docs/chat/docs/Message-Templates.md).
2. The Facebook Team approved or reject the template.
3. The Application send Approved WhatsApp message templates programmatically.
4. The Customer Received WhatsApp message template.


##### Customer Service Message

1. The Customer send message to WhatsApp Business API Phone number first.
2. The Application can send text and media message using API to Customer in the **24-hour window from last customer message**.
3. After 24-hour window, The Application can only send Notification Message using WhatsApp message templates.

#### Next Steps
Follow our [Get Started](https://docs.qontak.com/docs/chat/docs/Get-Started/Get-Started.md) guide to learn how to set up the WhatsApp Business API client and perform a basic API request.
