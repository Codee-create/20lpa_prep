# System Design Pattern & Architecture Reference

This reference guide summarizes the essential components, design patterns, and scalability choices tested in system design rounds.

---

## 🏗 1. System Design Building Blocks

### A. Load Balancers (LB)
*   **Purpose**: Distribute incoming network traffic across multiple application servers.
*   **Types**:
    *   **Layer 4 (L4) LB**: Operates at the transport layer (TCP/UDP). Routes traffic based on IP and Port. Fast, low resource usage.
    *   **Layer 7 (L7) LB**: Operates at the application layer (HTTP/HTTPS). Routes traffic based on headers, cookies, URL paths. Supports SSL termination.
*   **Algorithms**: Round Robin, Weighted Round Robin, Least Connections, IP Hash.

### B. Caching Strategies
*   **Patterns**:
    *   **Cache-Aside (Lazy Loading)**: App checks cache. If miss, queries database, updates cache, and returns. (Best for read-heavy workloads).
    *   **Write-Through**: App writes to cache. Cache writes to database synchronously. (Ensures data consistency).
    *   **Write-Back (Write-Behind)**: App writes to cache. Cache updates database asynchronously. (Very fast writes, risk of data loss on crash).
*   **Eviction Policies**: LRU (Least Recently Used), LFU (Least Frequently Used), FIFO, TTL (Time-To-Live expiration).

### C. Message Queues (MQ) & Pub/Sub
*   **Purpose**: Decouple microservices, enable asynchronous processing, and buffer spikes in traffic.
*   **Tools**:
    *   **RabbitMQ**: Standard message broker (AMQP). High reliability, complex routing, message acknowledgment.
    *   **Kafka Distributed Log**: High-throughput, distributed event streaming platform. Partition-based ordering, offset logs.
*   **Delivery Guarantees**: At-most-once, At-least-once, Exactly-once.

---

## 💾 2. Database Selection: SQL vs NoSQL

| Dimension | SQL (Relational) | NoSQL (Non-Relational) |
| :--- | :--- | :--- |
| **Data Model** | Tabular, structured (rows & columns) | Document, Key-Value, Wide-Column, Graph |
| **Schema** | Static, predefined schema | Dynamic, flexible schema |
| **Scaling** | Vertical (scale up) | Horizontal (scale out via sharding) |
| **Transactions** | ACID compliant (Strict Consistency) | BASE model (Eventual Consistency) |
| **Examples** | PostgreSQL, MySQL, Oracle | MongoDB, Cassandra, Redis, DynamoDB |

---

## ⚡ 3. Database Scaling & Sharding

*   **Replication**:
    *   **Active-Passive (Master-Slave)**: All writes go to Master, replicated to Slaves for reads. Promotes high read throughput.
    *   **Active-Active (Multi-Master)**: Writes to any node, syncs in background. Risk of conflicts.
*   **Sharding**: Horizontal partitioning of a database. Dividing rows across multiple database servers based on a shard key.
    *   *Range-based Sharding*: Shards based on key ranges (e.g. usernames A-M go to Shard 1). Leads to hot spots.
    *   *Hash-based Sharding*: Apply hash function to key (e.g. `hash(id) % 3`). Balances load but adding shards is expensive.
    *   *Consistent Hashing*: Maps shards and keys to a logical circle. Minimizes keys moved when scaling shards up/down (vital for CDNs and memcached).
