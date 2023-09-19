# Comments Service

The Comments Service is a microservice within a blog application that manages comments associated with blog posts. This service provides endpoints for retrieving and creating comments, as well as handling events related to comment moderation.

## Endpoints

### 1. Get Comments by Post ID
- **HTTP Method**: GET
- **Endpoint**: `/posts/:id/comments`
- **Description**: Retrieves comments associated with a specific blog post.
- **Parameters**:
  - `:id` (required): The ID of the blog post for which you want to retrieve comments.
- **Response**:
  - Status Code: 200 OK
  - Body: An array of comment objects or an empty array if no comments exist for the specified post.

### 2. Create Comment
- **HTTP Method**: POST
- **Endpoint**: `/posts/:id/comments`
- **Description**: Creates a new comment for a specific blog post.
- **Parameters**:
  - `:id` (required): The ID of the blog post to which the comment will be attached.
- **Request Body**:
  - `content` (required): The content of the comment.
- **Response**:
  - Status Code: 201 Created
  - Body: An array of comment objects, including the newly created comment.

### 3. Event Handling
- **HTTP Method**: POST
- **Endpoint**: `/events`
- **Description**: Handles events related to comment moderation. This endpoint receives events from other services and updates the status of comments accordingly.
- **Request Body**:
  - `type` (required): The type of event (e.g., "CommentModerated").
  - `data` (required): An object containing event-specific data, such as comment ID, status, content, etc.
- **Response**:
  - Status Code: 200 OK

## Usage

1. Start the Comments Service:
   ```bash
   node comments-service.js
   ```

2. The service will listen on port 4001 by default. Ensure that it is running and accessible.

## Dependencies

- `express`: A web application framework for Node.js.
- `body-parser`: Middleware for parsing request bodies.
- `crypto`: Node.js built-in module for generating random bytes.
- `cors`: Middleware for handling Cross-Origin Resource Sharing.
- `axios`: A promise-based HTTP client for making requests to other services.

## Event Handling

The Comments Service also handles events related to comment moderation. It listens for events like "CommentModerated" and updates the status of comments accordingly. When a comment is moderated, it sends a "CommentUpdated" event to inform other services about the status change.

---

This README provides an overview of the Comments Service and its endpoints. Please ensure that the service is properly configured and connected to other services in your microservices architecture. For more details on how to set up the entire blog application, refer to the documentation of the complete system.