# Query Service

The Query Service is a microservice responsible for querying and serving data to clients within a microservices-based blog application. This service provides an endpoint for retrieving blog posts along with their associated comments based on the data it receives from events.

## Endpoints

### 1. Get All Posts
- **HTTP Method**: GET
- **Endpoint**: `/posts`
- **Description**: Retrieves all blog posts along with their associated comments.
- **Response**:
  - Status Code: 200 OK
  - Body: An object containing post data, where each post includes an array of comments.

### 2. Event Handling
- **HTTP Method**: POST
- **Endpoint**: `/events`
- **Description**: Receives events related to post and comment creation and updates. It updates its local data based on the received events.
- **Request Body**: The event object with the following properties:
  - `type` (required): The type of the event (e.g., "PostCreated").
  - `data` (required): An object containing event-specific data.
- **Response**:
  - Status Code: 200 OK
  - Body: An empty response object.

## Event Handling Logic

The Query Service handles various events, including "PostCreated," "CommentCreated," and "CommentUpdated," and updates its internal data accordingly:

- When a "PostCreated" event is received, it adds a new post with its ID and title.
- When a "CommentCreated" event is received, it associates the comment with the corresponding post based on the post's ID.
- When a "CommentUpdated" event is received, it updates the content and status of the associated comment.

## Usage

1. Start the Query Service:
   ```bash
   node query-service.js
   ```

2. The service will listen on port 4002 by default. Ensure that it is running and accessible.

## Dependencies

- `express`: A web application framework for Node.js.
- `body-parser`: Middleware for parsing request bodies.
- `cors`: Middleware for handling Cross-Origin Resource Sharing.
- `axios`: A promise-based HTTP client for making requests to other services.

## Event Synchronization

Upon starting, the Query Service synchronizes its data with the event history by fetching events from the Event Bus Service (http://localhost:4005/events). This ensures that the service has the most up-to-date data about posts and comments to serve to clients.

## Event-Driven Architecture

This service is designed to work within an event-driven architecture, where microservices communicate via events. It listens for events and updates its local data accordingly, allowing for real-time data synchronization between services.

---

This README provides an overview of the Query Service and its event handling logic. Ensure that the service is properly configured and connected to other microservices in your architecture to enable data querying and retrieval in your microservices-based blog application.