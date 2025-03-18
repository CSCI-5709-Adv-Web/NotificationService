### Notification Service

## Overview

The Notification Service manages all communications and alerts for the Commune Drop platform. It sends real-time notifications to users and carriers about order status changes, account updates, and other important events through multiple channels including push notifications, SMS, and email.

## Features

- Multi-channel notification delivery (push, SMS, email)
- Templated notification content
- Delivery status tracking
- User notification preferences
- Scheduled and triggered notifications
- Batch processing for high-volume scenarios
- Notification history and analytics

## Dependencies

- Auth Service: For user authentication and profile information
- Order Service: For order status updates
- External Providers: SMS gateway, email service, push notification service

## Technology Stack

- Runtime: Node.js
- Framework: Express.js
- Database: MongoDB
- Message Queue: RabbitMQ/Kafka for event processing
- Caching: Redis
- Push Notifications: Firebase Cloud Messaging (FCM) / Apple Push Notification Service (APNS)
- SMS: Twilio / Nexmo / AWS SNS
- Email: SendGrid / Mailgun / AWS SES

## Setup

### Prerequisites

- Node.js v16+
- MongoDB
- Redis
- RabbitMQ/Kafka
- API keys for notification providers

### Quick Start

1. Clone the repository

```shellscript
git clone https://github.com/commune-drop/notification-service.git
cd notification-service
```

2. Install dependencies

```shellscript
npm install
```

3. Configure environment variables

```shellscript
cp .env.example .env
# Edit .env with your configuration
```

4. Start the service

```shellscript
npm start
```

For development:

```shellscript
npm run dev
```

## Configuration

Key environment variables:

```plaintext
PORT=3005
MONGODB_URI=mongodb://localhost:27017/notification-service
AUTH_SERVICE_URL=http://auth-service:3000
ORDER_SERVICE_URL=http://order-service:3001
RABBITMQ_URL=amqp://localhost:5672
REDIS_URL=redis://localhost:6379
FCM_SERVER_KEY=your_fcm_server_key
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
SENDGRID_API_KEY=your_sendgrid_api_key
```

## Notification Channels

The service supports multiple notification channels:

- Push notifications for mobile devices
- SMS for urgent alerts
- Email for detailed information
- In-app notifications for active users

## Notification Templates

Pre-defined templates for common scenarios:

- Order status updates
- Payment confirmations
- Delivery ETAs
- Account alerts
- Promotional messages
- System announcements

## Event Handling

The service listens for events from other services:

- Order status changes
- Payment processing
- User account updates
- Carrier location updates
- System alerts

## Delivery Tracking

Each notification is tracked through its lifecycle:

- Queued
- Sent
- Delivered
- Read
- Failed

## Retry Mechanism

Failed notifications are handled with:

- Configurable retry attempts
- Exponential backoff
- Fallback channels
- Dead letter queue for manual review

## License

MIT
