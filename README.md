# Notification Service

A backend service for sending and managing notifications across multiple channels (Email, SMS, and in-app).

## Features

- Send notifications via API endpoint
- Retrieve user notifications via API endpoint
- Support for multiple notification types (Email, SMS, in-app)
- Queue system for processing notifications
- Retry mechanism for failed notifications

## API Endpoints

### Send a Notification

\`\`\`
POST /api/notifications
\`\`\`

Request body:
\`\`\`json
{
  "userId": "user123",
  "title": "Notification Title",
  "message": "Notification message content",
  "type": "email" // or "sms" or "in-app"
}
\`\`\`

Response:
\`\`\`json
{
  "message": "Notification queued successfully",
  "notificationId": "uuid-here"
}
\`\`\`

### Get User Notifications

\`\`\`
GET /api/users/{id}/notifications
\`\`\`

Response:
\`\`\`json
{
  "notifications": [
    {
      "id": "notification-id",
      "userId": "user123",
      "title": "Notification Title",
      "message": "Notification message content",
      "type": "email",
      "status": "sent",
      "createdAt": "2023-05-17T20:58:57.000Z"
    }
  ]
}
\`\`\`

## Setup Instructions

1. Clone the repository
   \`\`\`
   git clone https://github.com/yourusername/notification-service.git
   cd notification-service
   \`\`\`

2. Install dependencies
   \`\`\`
   npm install
   \`\`\`

3. Run the development server
   \`\`\`
   npm run dev
   \`\`\`

4. Open [http://localhost:3000](https://v0-assignment-recreation.vercel.app/) in your browser to see the application

## Implementation Details

### In-Memory Database

For demonstration purposes, this project uses an in-memory database. In a production environment, you would want to use a proper database like PostgreSQL, MongoDB, etc.

### Queue System

The project implements a simple in-memory queue system to demonstrate the concept of asynchronous notification processing. In a production environment, you would want to use a proper message queue like RabbitMQ, Kafka, or a cloud service like AWS SQS.

### Retry Mechanism

Failed notifications are automatically retried up to 3 times with a delay between retries. This helps ensure notifications are delivered even if there are temporary issues with the notification channels.

## Assumptions Made

1. Authentication and authorization are handled by a separate service
2. User information is stored in a separate service/database
3. For demonstration purposes, notification delivery is simulated
4. In a production environment, you would integrate with actual email/SMS services

## Future Improvements

1. Add authentication and authorization
2. Implement rate limiting
3. Add notification templates
4. Add notification preferences for users
5. Implement notification batching for efficiency
6. Add analytics for notification delivery and open rates
