# TelegramSender Component Documentation

## Overview

The TelegramSender component enables sending messages through the Telegram Bot API.

## Component Specifications

- **Display Name**: Telegram Bot Message
- **Description**: Send messages via Telegram Bot API
- **Icon**: message-square

## Inputs

| Name      | Type             | Description                     | Mode |
| --------- | ---------------- | ------------------------------- | ---- |
| bot_token | MessageTextInput | Telegram Bot API Token          | Tool |
| chat_id   | MessageTextInput | Chat ID for message destination | Tool |
| message   | MessageTextInput | Message content to send         | Tool |

## Output

| Name   | Display Name | Method       |
| ------ | ------------ | ------------ |
| output | Response     | build_output |

## Usage Example

```python
from langflow.custom import Component

# Initialize component
telegram_sender = TelegramSenderComponent()

# Set required parameters
telegram_sender.bot_token = "YOUR_BOT_TOKEN"
telegram_sender.chat_id = "CHAT_ID"
telegram_sender.message = "Hello from Langflow!"

# Send message
response = telegram_sender.build_output()
```

## Error Handling

- Returns response data on successful message delivery
- Returns error message as string if request fails
- Updates component status with response/error data

## API Details

- Endpoint: `https://api.telegram.org/bot{token}/sendMessage`
- Method: GET
- Parameters:
  - chat_id: Recipient chat identifier
  - text: Message content to send
