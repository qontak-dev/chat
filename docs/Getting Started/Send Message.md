# Send Message

## Flow

![Bot-Send-Message](../../assets/images/Bot-Send-Message.png "Flow Bot Send Message")

## Send Message

Send Text Message to customer within window session.

```bash
curl --request POST \
  --url https://chat-service.qontak.com/api/open/v1/messages/whatsapp/bot \
  --header 'Authorization: Bearer ${ACCESS_TOKEN}' \
  --header 'Content-Type: application/json'
  --data-raw '{
    "room_id": "<uuid_room>",
    "type": "text",
    "text": "<String>"
  }'
```


