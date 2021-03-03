# Message Interaction

## Incoming Message From Customer
- `receive_message_from_customer` : send webhook when customer send message

### Flow

![customer-send-message](../../assets/images/Customer-Send-Message.png "Customer Send Message")

### Enable Message Coming from Customer
```bash
curl --location --request PUT 'https://chat-service.qontak.com/api/open/v1/message_interactions' \
--header 'Authorization: Bearer WPuW1u-v21SkfqfC7NNBD9NvNg3ojy8ftuUpVy3rbU' \
--header 'Content-Type: application/json' \
--data-raw '{
  "receive_message_from_agent": false,
  "receive_message_from_customer": true,
  "status_message": false,
  "url": "https://webhook.site/498b30f1-e74e-4bd2-b20e-9c1fea536a22"
}'
```

### Response
```json
{
    "status": "success",
    "data": {
        "auto_assign_agent": false,
        "auto_responder_in_office_hours": {
            "enabled": true,
            "message": "Halo, terima kasih telah menghubungi Qontak.com\nBisa sebutkan nama dan dari perusahaan apa?\nKami akan segera membalas pesan Anda.\n"
        },
        "auto_responder_out_office_hours": {
            "enabled": true,
            "message": "Halo, terima kasih telah menghubungi Qontak.com\n\nKami akan segera membalas pesan Anda.\n"
        },
        "agent_can_takeover": true,
        "custom_agent_allocation": {
            "enabled": false,
            "webhooks": [
                {
                    "id": "8af75000-ffd0-494c-b953-4d3bdcb3057a",
                    "event": "custom_agent_allocation",
                    "url": ""
                }
            ]
        },
        "agent_assigned_to_room": {
            "enabled": false,
            "webhooks": []
        },
        "agent_unassigned_from_room": {
            "enabled": false,
            "webhooks": []
        },
        "room_resolved": {
            "enabled": false,
            "webhooks": []
        },
        "receive_message_from_agent": {
            "enabled": false,
            "webhooks": [
                {
                    "id": "9f544cd4-33cc-4e61-b074-e52984e6b090",
                    "event": "message_interaction",
                    "url": "https://webhook.site/498b30f1-e74e-4bd2-b20e-9c1fea536a22"
                }
            ]
        },
        "receive_message_from_customer": {
            "enabled": true,
            "webhooks": [
                {
                    "id": "9f544cd4-33cc-4e61-b074-e52984e6b090",
                    "event": "message_interaction",
                    "url": "https://webhook.site/498b30f1-e74e-4bd2-b20e-9c1fea536a22"
                }
            ]
        },
        "status_message": {
            "enabled": false,
            "webhooks": [
                {
                    "id": "9f544cd4-33cc-4e61-b074-e52984e6b090",
                    "event": "message_interaction",
                    "url": "https://webhook.site/498b30f1-e74e-4bd2-b20e-9c1fea536a22"
                }
            ]
        }
    }
}
```

### Receive Webhook from Customer Send Message

```json
{
    "id": "4198c4b2-d39d-45b5-ac9c-89bccb9513ec",
    "type": "text",
    "room_id": "e658411a-99aa-417d-8c6f-40e1594554a7",
    "is_campaign": false,
    "sender_id": "9c682ecf-6149-4d23-b6ae-d3c872194d58",
    "sender_type": "Models::Contact",
    "sender": {
        "name": "Burhanudin",
        "avatar": null
    },
    "participant_id": "64c4be1f-916b-4e5e-a8cd-52ec2cbb082f",
    "organization_id": "5c8521e5-5978-4817-9ceb-ae1710d676c9",
    "text": "helo",
    "status": "created",
    "participant_type": "customer",
    "external_id": "ABEGYoEXZhAAAgo-sInteMYC-oMQ",
    "local_id": null,
    "created_at": "2021-03-03T22:53:29.000Z",
    "reply": null,
    "room": {
        "id": "e658411a-99aa-417d-8c6f-40e1594554a7",
        "name": "Burhanudin",
        "description": "",
        "status": "unassigned",
        "type": "Models::CustomerServiceRoom",
        "tags": [],
        "channel": "wa",
        "channel_account": "Qontak",
        "organization_id": "5c8521e5-5978-4817-9ceb-ae1710d676c9",
        "account_uniq_id": "628117661000",
        "channel_integration_id": "b3a2ee0b-7dac-47b8-a115-7bc63abf8f15",
        "session": "open",
        "session_at": "2021-03-03T22:53:29.000Z",
        "unread_count": 2,
        "created_at": "2021-03-03T22:36:08.196Z",
        "updated_at": "2021-03-03T22:36:08.196Z",
        "avatar": null,
        "resolved_at": null,
        "external_id": null,
        "resolved_by_id": null,
        "resolved_by_type": null
    }
}
```


## Send Message to Customer

- `status_message` : send webhook if message status is change (created, sent, delivered, read)

### Flow

![send-message-to-customer](../../assets/images/Send-Message-to-Customer.png "Send-message to customer")

### Enable Webhook Send Message to Customer
```bash
curl --location --request PUT 'https://chat-service.qontak.com/api/open/v1/message_interactions' \
--header 'Authorization: Bearer WPuW1u-v21SkfqfC7NNBD9NvNg3ojy8ftuUpVy3rbU' \
--header 'Content-Type: application/json' \
--data-raw '{
  "receive_message_from_agent": false,
  "receive_message_from_customer": false,
  "status_message": true,
  "url": "https://webhook.site/498b30f1-e74e-4bd2-b20e-9c1fea536a22"
}'
```

### Receive Webhook Status Message send from Agent
```json
{
    "id": "d27cc7ac-8281-438d-9cea-e74e627cea32",
    "type": "text",
    "room_id": "e658411a-99aa-417d-8c6f-40e1594554a7",
    "is_campaign": false,
    "sender_id": "84d627bf-3f71-48de-bd4d-b623ad19857a",
    "sender_type": "Models::User",
    "sender": {
        "name": "Agent One",
        "avatar": {
            "url": "https://qontak-hub-production.s3-ap-southeast-1.amazonaws.com/assets/qi-user.png",
            "large": {
                "url": "https://qontak-hub-production.s3-ap-southeast-1.amazonaws.com/assets/qi-user.png"
            },
            "medium": {
                "url": "https://qontak-hub-production.s3-ap-southeast-1.amazonaws.com/assets/qi-user.png"
            },
            "small": {
                "url": "https://qontak-hub-production.s3-ap-southeast-1.amazonaws.com/assets/qi-user.png"
            },
            "filename": null,
            "size": 0
        }
    },
    "participant_id": "8c10c529-360d-4880-90bf-85ccf51160a6",
    "organization_id": "5c8521e5-5978-4817-9ceb-ae1710d676c9",
    "text": "ada yang bisa dibantu?",
    "status": "read",
    "participant_type": "agent",
    "external_id": "gBEGYoEXZhAAAglXDyY42p1Do6I",
    "local_id": null,
    "created_at": "2021-03-03T23:00:33.492Z",
    "reply": null,
    "room": {
        "id": "e658411a-99aa-417d-8c6f-40e1594554a7",
        "name": "Burhanudin",
        "description": "",
        "status": "assigned",
        "type": "Models::CustomerServiceRoom",
        "tags": [],
        "channel": "wa",
        "channel_account": "Qontak",
        "organization_id": "5c8521e5-5978-4817-9ceb-ae1710d676c9",
        "account_uniq_id": "628117661000",
        "channel_integration_id": "b3a2ee0b-7dac-47b8-a115-7bc63abf8f15",
        "session": "open",
        "session_at": "2021-03-03T22:55:52.000Z",
        "unread_count": 0,
        "created_at": "2021-03-03T22:36:08.196Z",
        "updated_at": "2021-03-03T22:55:13.670Z",
        "avatar": null,
        "resolved_at": null,
        "external_id": null,
        "resolved_by_id": null,
        "resolved_by_type": null
    }
}
```

### Receive Webhook sent status from Broadcast / Broadcast API
```json
{
    "id": "a9fb2a77-62da-4100-a770-6f6fc8bc36de",
    "type": "text",
    "room_id": "e658411a-99aa-417d-8c6f-40e1594554a7",
    "is_campaign": true,
    "sender_id": "2fcf11ac-5d78-475a-9000-fea426e3c270",
    "sender_type": "Models::SystemAccount",
    "sender": {
        "name": "Bot",
        "avatar": null
    },
    "participant_id": "9de18858-00d7-4114-939e-7bd95c5e0e3b",
    "organization_id": "5c8521e5-5978-4817-9ceb-ae1710d676c9",
    "text": "Kepada Yth Customer Burhanudin,\nTagihan anda akan segera jatuh tempo, mohon segera lakukan pembayaran.\n-MIC Finance",
    "status": "sent",
    "participant_type": "bot",
    "external_id": "gBEGYoEXZhAAAgkDd8uUC103idc",
    "local_id": null,
    "created_at": "2021-03-03T23:06:36.452Z",
    "reply": null,
    "room": {
        "id": "e658411a-99aa-417d-8c6f-40e1594554a7",
        "name": "Burhanudin",
        "description": "",
        "status": "assigned",
        "type": "Models::CustomerServiceRoom",
        "tags": [],
        "channel": "wa",
        "channel_account": "Qontak",
        "organization_id": "5c8521e5-5978-4817-9ceb-ae1710d676c9",
        "account_uniq_id": "628117661000",
        "channel_integration_id": "b3a2ee0b-7dac-47b8-a115-7bc63abf8f15",
        "session": "open",
        "session_at": "2021-03-03T22:55:52.000Z",
        "unread_count": 0,
        "created_at": "2021-03-03T22:36:08.196Z",
        "updated_at": "2021-03-03T22:55:13.670Z",
        "avatar": null,
        "resolved_at": null,
        "external_id": null,
        "resolved_by_id": null,
        "resolved_by_type": null
    }
}
```