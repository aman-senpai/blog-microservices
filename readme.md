# Microservices-Based Blog Application

The Microservices-Based Blog Application is a distributed and event-driven system that enables users to create and interact with blog posts and comments. This application is built using a microservices architecture, allowing for flexibility, scalability, and modularity in the development and deployment of its components.

## Features

### 1. Blog Posts
- Users can create, read, update, and delete blog posts.
- Posts can contain text, images, or other multimedia content.
- Each post can have multiple comments associated with it.

### 2. Comments
- Users can add comments to blog posts.
- Comment moderation is implemented to ensure content quality and user safety.
- Comments can be approved or rejected based on moderation criteria.

### 3. Event-Driven Communication
- The application utilizes an Event Bus Service for inter-microservice communication.
- Microservices communicate by publishing and subscribing to events.
- Real-time data synchronization is achieved through events.

## Microservices Overview

The Microservices-Based Blog Application is composed of several microservices, each with its specific responsibilities:

1. **Posts Service**: Manages blog posts and their associated comments. Provides endpoints for creating, retrieving, updating, and deleting posts.

   - Commit: `8940f8b` - Implement ingress-nginx controller and connect all the services to the right ports

2. **Comments Service**: Handles comments for blog posts. Allows users to create comments, retrieve comments for a specific post, and handles events related to comment moderation.

   - Commit: `2ab40b2` - Complete Comment Moderation Service

3. **Comment Moderation Service**: Moderates comments based on content criteria. Approves or rejects comments and sends updated events.

   - Commit: `3813a08` - Implement Event Sync

4. **Query Service**: Serves as a query interface to retrieve blog posts and their associated comments. It listens for events and updates its data for efficient querying.

   - Commit: `fea1e14` - Implement query service

5. **Event Bus Service**: Facilitates communication between microservices by allowing them to publish and subscribe to events. It ensures that events are distributed to relevant microservices.

   - Commit: `ad72af5` - Create event bus

## Usage

1. The dev server is setup using skaffold
2. To run this you'll need skaffold installed in your system install it from [here](https://skaffold.dev/docs/install/).

   ```bash
   # 
   skaffold dev
   ```


## Dependencies

The Microservices-Based Blog Application relies on the following dependencies:

- `express`: A web application framework for Node.js.
- `body-parser`: Middleware for parsing request bodies.
- `cors`: Middleware for handling Cross-Origin Resource Sharing.
- `axios`: A promise-based HTTP client for making requests to other services.

## Event-Driven Architecture

The core architecture of this blog application is event-driven. Events are used for communication between microservices, ensuring real-time data updates and synchronization.

## Moderation Criteria

The application's moderation criteria for comments can be customized to fit your specific requirements. In the provided code, comments containing the word "orange" are automatically rejected as an example.

## Conclusion

The Microservices-Based Blog Application showcases a powerful, event-driven microservices architecture for building scalable and resilient web applications. It provides flexibility in adding new features and scaling individual components to meet growing demands.

Please refer to the individual README files for each microservice for more detailed information on how to use and configure them within the application.

```
   # This is learning project.
```