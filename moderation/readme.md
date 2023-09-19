# Comment Moderation Service

The Comment Moderation Service is responsible for moderating comments created in a microservices-based blog application. It receives comments, checks their content, and decides whether to approve or reject them based on specific criteria.

## Endpoints

### 1. Event Handling
- **HTTP Method**: POST
- **Endpoint**: `/events`
- **Description**: Receives events related to comments and performs moderation based on content criteria.
- **Request Body**: The event object with the following properties:
  - `type` (required): The type of the event (e.g., "CommentCreated").
  - `data` (required): An object containing event-specific data.
- **Response**:
  - Status Code: 200 OK
  - Body: An empty response object.

## Comment Moderation Logic

The Comment Moderation Service checks the content of comments to determine whether they should be approved or rejected. The logic is as follows:

- If the comment content includes the word "orange," it is marked as "rejected."
- Otherwise, the comment is marked as "approved."

The service then generates a "CommentModerated" event with the updated status and forwards it to the Event Bus Service for distribution to other microservices.

## Usage

1. Start the Comment Moderation Service:
   ```bash
   node comment-moderation-service.js
   ```

2. The service will listen on port 4003 by default. Ensure that it is running and accessible.

## Dependencies

- `express`: A web application framework for Node.js.
- `body-parser`: Middleware for parsing request bodies.
- `axios`: A promise-based HTTP client for making requests to other services.

## Event Forwarding

The Comment Moderation Service forwards moderated comments to the Event Bus Service using HTTP POST requests. The Event Bus Service is responsible for distributing these events to other microservices in the architecture.

## Moderation Criteria

The moderation criteria used in this service are just an example. In a real-world application, you may have more sophisticated moderation rules and mechanisms to ensure the quality of comments.

---

This README provides an overview of the Comment Moderation Service and its event handling logic. Ensure that the service is properly configured and connected to the Event Bus Service to enable comment moderation in your microservices-based blog application.