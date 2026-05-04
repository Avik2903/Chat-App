# 🚀 Scalable Real-Time Chat Application (Microservices Architecture)

A production-inspired **real-time chat system** built using a **microservices architecture**, designed to demonstrate scalable backend design, event-driven communication, and low-latency messaging.

---

## 🧠 Overview

This project simulates how modern chat systems (like WhatsApp/Slack) are built at scale. It separates responsibilities across independent services and uses **WebSockets + event queues + caching** to handle real-time communication reliably.

---

## ⚡ Key Features

### 💬 Real-Time Messaging

* Bi-directional communication using **WebSockets (Socket.io)**
* Low latency message delivery
* Room-based communication for conversations

---

### ✍️ Typing Indicators

* Real-time `user_typing` and `user_stopped_typing` events
* Debounced to prevent excessive network calls
* Automatically expires using timeout fallback

---

### ✅ Read Receipts & Message Status

* Tracks message lifecycle:

  * `sent → delivered → seen`
* Supports multi-user tracking:

  ```ts
  seenBy: [userId],
  deliveredTo: [userId]
  ```
* Ensures **database is the source of truth**

---

### 🔄 Event-Driven Architecture

* Services communicate asynchronously via **RabbitMQ**
* Example flows:

  * User registration → email event → mail service processes
  * Message sent → notification event triggered

---

### ⚡ Redis Integration

* Used for:

  * Caching frequently accessed data
  * Scaling WebSocket connections (pub/sub model)
* Enables horizontal scalability

---

### 🗄️ Persistent Storage

* MongoDB used for:

  * User data
  * Chat messages
* Ensures durability and consistency

---

## 🔄 System Flow

### 📩 Sending a Message

```
1. Client sends message → Chat Service
2. Message stored in MongoDB
3. WebSocket emits message to receiver(s)
4. Receiver acknowledges delivery
5. Status updated in DB (delivered/seen)
```

---

### 👀 Read Receipt Flow

```
1. Receiver opens chat
2. Client emits "message_seen"
3. Server updates DB (seenBy array)
4. Event broadcast to sender
```

---

### ✍️ Typing Indicator Flow

```
1. User starts typing → emit "typing"
2. Other users see typing indicator
3. Stop typing / timeout → emit "stop_typing"
```

---

## 🛠️ Tech Stack

### Backend

* Node.js
* Express.js

### Real-Time Communication

* Socket.io

### Database

* MongoDB

### Caching & Pub/Sub

* Redis

### Message Queue

* RabbitMQ

---

## 📦 Project Structure

```
/chat-service
  ├── controllers/
  ├── models/
  ├── sockets/
  └── config/

/user-service
  ├── controllers/
  ├── middleware/
  └── models/

/mail-service
  ├── consumer/
  └── queue/
```

---

## 🚀 Getting Started

### Prerequisites

* Node.js
* MongoDB
* Redis
* RabbitMQ

---

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/Chat-App.git

# Install dependencies for each service
cd chat && npm install
cd user && npm install
cd mail && npm install
```

---

### Running Services

Run each service independently:

```bash
npm run dev
```

---

## 📈 Scalability Considerations

* Stateless services for horizontal scaling
* Redis pub/sub for socket synchronization across instances
* Event-driven communication reduces tight coupling
* Database as single source of truth for consistency

---

## 🧪 Future Improvements

* API Gateway integration
* Docker & Kubernetes deployment
* Rate limiting & security hardening
* Push notifications
* Group chat & media sharing

---

## 🎯 Key Learnings

* Designing **distributed systems**
* Handling **real-time communication at scale**
* Managing **eventual consistency**
* Building **fault-tolerant microservices**

---

## ⭐ Final Note

This project focuses on **backend system design over UI**, emphasizing how real-world messaging systems are architected for **scalability, reliability, and performance**.

---
