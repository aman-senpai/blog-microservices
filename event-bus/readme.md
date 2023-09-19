# Event Bus

The Event Bus Service is a central component in a microservices architecture that facilitates communication between different microservices by allowing them to publish and subscribe to events. This service receives events from various sources and distributes them to the relevant microservices.

## Endpoints

### 1. Publish Event
- **HTTP Method**: POST
- **Endpoint**: `/events`
- **Description**: Receives events from other microservices and broadcasts them to all subscribed microservices.
- **Request Body**: The event object with the following properties:
  - `type` (required): The type of the event (e.g., "CommentCreated").
  - `data` (required): An object containing event-specific data.
- **Response**:
  - Status Code: 200 OK
  - Body: An acknowledgment response with a "status" property set to "Ok!".

### 2. Get Events
- **HTTP Method**: GET
- **Endpoint**: `/events`
- **Description**: Retrieves a list of all events that have been received and processed by the Event Bus Service.
- **Response**:
  - Status Code: 200 OK
  - Body: An array of event objects.

## Usage

1. Start the Event Bus Service:
   ```bash
   node event-bus-service.js
   ```

2. The service will listen on port 4005 by default. Ensure that it is running and accessible.

## Event Distribution

The Event Bus Service is responsible for distributing events to other microservices in your architecture. It forwards events to the following services by making HTTP POST requests:

- Service 1: http://localhost:4000/events
- Service 2: http://localhost:4001/events
- Service 3: http://localhost:4002/events
- Service 4: http://localhost:4003/events

Make sure that these services are running and configured to handle incoming events.

## Dependencies

- `express`: A web application framework for Node.js.
- `body-parser`: Middleware for parsing request bodies.
- `axios`: A promise-based HTTP client for making requests to other services.

## Event Logging

Events received by the Event Bus Service are logged in memory and can be retrieved using the "/events" endpoint. This can be useful for monitoring and debugging purposes.

---

This README provides an overview of the Event Bus Service and its endpoints. Ensure that the service is properly configured and connected to other microservices in your architecture to enable event-driven communication.

Please refer to the documentation of individual microservices for more details on how events are handled and processed within each service.