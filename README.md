# 🚀 Logging & Monitoring Microservice System

A scalable, distributed Logging & Monitoring platform built with Rust, Node.js, Redis Streams, and PostgreSQL.
Designed for high-throughput log ingestion, secure authentication, real-time processing, and developer-friendly SDKs.

   >  Goal: Centralized, secure, and scalable logging for modern microservice architectures.

🧠 High-Level Architecture
```
Client Apps / Services
        │
        ▼
 Node.js SDK (Express Middleware)
        │
        ▼
   API Gateway
        │
        ▼
 Ingest API Service (Rust)
        │
        ▼
 Redis Streams (Buffer & Queue)
        │
        ▼
 Collector Service (Rust)
        │
        ▼
 PostgreSQL (Persistent Storage)
        │
        ▼
 Real-time Monitoring (WebSocket)
```
## 🧩 Services Overview

1️⃣ Auth Service (Node.js + TypeScript)

**Handles authentication, user management, and API key issuance.**

### Responsibilities
- User registration & authentication
- API key generation
- JWT-based authorization
- Secure password hashing

### Tech Stack

    - Node.js + Express
    - TypeScript
    - PostgreSQL
    - JWT

📁 Repo: [Auth_Service](https://github.com/DeveloperWK/log-auth-service.git)

2️⃣ Ingest API Service (Rust)

**High-performance log ingestion service.**

### Responsibilities

    - Validate API keys (HMAC-based)
    - Accept logs from SDK & clients
    - Push logs to Redis Streams
    - Stateless & horizontally scalable

### Tech Stack

    - Rust
    - Redis Streams
    - Async I/O

📁 Repo: [Ingest_API_Service](https://github.com/DeveloperWK/log-ingest-api.git)

3️⃣ Collector Service (Rust)

**Consumes logs from Redis Streams and persists them.**

### Responsibilities

    - Redis Stream consumer group
    - Batch processing
    - Store logs in PostgreSQL
    - Real-time WebSocket streaming

### Tech Stack

    - Rust
    - Redis Streams
    - PostgreSQL

📁 Repo: [Collector_Service](https://github.com/DeveloperWK/log-collector-service.git)

4️⃣ API Gateway (NGINX)

**Single entry point for all external traffic, powered by a high-performance reverse proxy.**

### Responsibilities

- Route incoming requests to internal microservices
- Centralized access control and request forwarding
- Hide internal service topology from clients
- Enable rate limiting, buffering, and basic security rules
- Act as a lightweight edge layer before Rust services

> Why NGINX

1. Extremely fast and memory-efficient
2. Perfect for high-throughput log ingestion
3. Simple configuration for reverse proxying
4. No extra runtime overhead compared to Node.js

### Tech Stack

    - NGINX
    - Reverse Proxy
    - HTTP / WebSocket support

📁 Config Repo: [gateway (NGINX configuration)](https://github.com/DeveloperWK/log-nginx-gateway.git)

5️⃣ Node.js SDK (Express Middleware)

**Developer-friendly SDK for easy integration.**

> Features

    - Automatic request/response logging
    - Context propagation (trace_id, span_id)
    - Non-blocking log batching
    - Plug-and-play Express middleware

### Tech Stack

    - Node.js
    - TypeScript
    - ES Modules

📁 Repo: [SDK_node_express](https://github.com/DeveloperWK/log-SDK-node-express.git)

## 🗂️ Monorepo Index (This Repository)

This repository acts as a central documentation hub, linking all services:
```
Logging + Monitoring Microservice System
├── Auth_Service
├── Ingest_API_Service
├── Collector_Service
├── gateway
├── SDK_node_express
└── README.md (this file)
```

> Each service is maintained as an independent repository for:

    - Clear ownership
    - Independent scaling
    - Separate deployment pipelines

## 🛠️ Core Technologies

    Rust →  High-performance ingestion & processing
    Node.js + TypeScript →  Auth, SDK
    Redis Streams →  Durable log buffering
    PostgreSQL →  Long-term storage
    WebSockets →  Real-time monitoring
    HMAC + JWT →  Secure authentication

### 🔐 Security Design

    - API Key + HMAC validation
    - JWT-based user authentication
    - Isolated internal services
    - Gateway-level traffic control
    - Backpressure via Redis Streams

> 📈 Why Redis Streams?

    - Handles burst traffic
    - Prevents data loss
    - Enables consumer groups
    - Decouples ingestion from storage
    - Perfect for logging pipelines

### 🚧 Current Status

    ✅ Core services implemented

    ✅ SDK available (Note: Node SDK has been created, SDKs for other languages ​​will be created.)

    ✅ Redis Stream pipeline working

    🚧 Dashboard UI (planned)

    🚧 Real-time monitoring (planned)

    🚧 Alerting & metrics (planned)

> 👤 Author
>
> MD. Wasiful Kabir (Developer.WK)
>
> Backend-Focused Full-Stack Developer

    - GitHub: https://github.com/DeveloperWK
    - Portfolio: https://developer-wk.vercel.app
    - LinkedIn: https://www.linkedin.com/in/md-wasiful-kabir

    “ONE STEP AHEAD OF EVERYONE.”

### 📌 Next Improvements (Planned)

    - Log querying & filtering API
    - Grafana / Prometheus integration
    - Alert rules & notifications
    - Multi-tenant isolation
    - Kubernetes deployment

