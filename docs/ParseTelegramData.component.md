# ParseData Component Documentation

## Overview

The ParseData component is designed to process Telegram webhook data, extracting message text and chat ID from incoming messages.

## Features

- Extracts message text from Telegram webhook data
- Retrieves chat ID from message data
- Handles both single and list-formatted webhook data
- Provides error handling and status updates

## Component Specifications

- **Display Name**: Parse Data
- **Description**: Extract message text and chat ID from Telegram webhook data
- **Icon**: braces

## Inputs

| Name | Type      | Description           |
| ---- | --------- | --------------------- |
| data | DataInput | Webhook data to parse |

## Outputs

| Name    | Display Name | Method      |
| ------- | ------------ | ----------- |
| chat_id | Chat ID      | get_chat_id |
| message | Message Text | parse_data  |

## Usage Example

```python
from langflow.custom import Component

# Initialize component
parse_data = ParseDataComponent()

# Sample webhook data
webhook_data = {
    "data": {
        "message": {
            "text": "Hello World",
            "chat": {
                "id": 123456789
            }
        }
    }
}

# Set component data
parse_data.data = webhook_data

# Extract message text
message = parse_data.parse_data()  # Returns Message object with text="Hello World"

# Extract chat ID
chat_id = parse_data.get_chat_id()  # Returns Message object with text="123456789"
```

## Error Handling

The component includes error handling for both parsing operations:

- Returns status messages indicating success or failure
- Raises ValueError with detailed error message on failure
- Handles both single data objects and lists of data

## Implementation Notes

- Input data should follow Telegram webhook format
- Component processes first item if data is provided as list
- Both outputs are returned as Message objects with string content
