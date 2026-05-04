🚀 Scalable Chat Application (Microservices-Based)

This project is a real-time chat application designed using a microservices architecture to simulate production-grade backend systems. It focuses on scalability, real-time communication, and event-driven design.

🧩 Architecture Overview

The system is split into independent services:

User Service – Handles authentication, user management, and authorization
Chat Service – Manages conversations, messages, and real-time communication via WebSockets
Mail Service – Processes asynchronous tasks like sending emails using event consumers

⚡ Key Features

Real-time messaging using WebSockets (Socket.io)
Typing indicators for live user interaction
Read receipts & message status tracking
Event-driven communication between services
Scalable architecture with Redis and message queue integration
Persistent storage using MongoDB

🔄 System Flow

User sends a message via client
Chat service processes and stores the message
WebSocket event broadcasts message to recipients
Read receipts and typing events are handled in real-time
Async events (e.g., notifications) are processed by the mail service

🛠️ Tech Stack

Backend: Node.js, Express
Realtime: Socket.io
Database: MongoDB
Caching / Pub-Sub: Redis
Messaging Queue: RabbitMQ (event-driven communication)

📈 Highlights

Designed with scalability in mind (multi-service architecture)
Implements real-time communication patterns used in production systems
Demonstrates understanding of distributed systems and async processing
