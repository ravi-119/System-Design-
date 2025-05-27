# System Design Notes

## What is System Design?

System Design is the process of defining the architecture, components, modules, interfaces, and data for a system to satisfy specified requirements. It involves high-level planning followed by detailed planning and execution to build scalable and reliable systems.

---

## Importance of System Design

- Enables building scalable and maintainable systems.
- Helps in making informed engineering decisions.
- Essential for handling large-scale applications and distributed systems.

---

## System Design Life Cycle

1. **Requirements Gathering**
   - Functional Requirements
   - Non-Functional Requirements

2. **Prioritization/Phasing**

3. **Infrastructure Estimation**
   - Storage
   - Computation
   - Network
   - Components
   - Communication

---

## HLD vs LLD

### High Level Design (HLD)

- **Definition:** HLD provides a bird's eye view of the overall system architecture. It outlines the system's main components, their relationships, and how they interact.
- **Focus:** Architecture, modules, data flow, technology stack, and external interfaces.
- **Purpose:** To communicate the system's structure and design approach to stakeholders and developers.
- **Artifacts:** Block diagrams, architecture diagrams, component diagrams.

**Example Topics in HLD:**
- System architecture (Monolithic, SOA, Microservices)
- Load balancer placement
- Database selection (SQL/NoSQL)
- High-level data flow

### Low Level Design (LLD)

- **Definition:** LLD breaks down the components defined in HLD into detailed designs. It specifies the logic, algorithms, data structures, and class diagrams for each module.
- **Focus:** Internal logic, detailed workflows, API contracts, database schema, and class-level design.
- **Purpose:** To guide developers in implementing each component.
- **Artifacts:** Class diagrams, sequence diagrams, detailed pseudo-code, API specifications.

**Example Topics in LLD:**
- Class and method definitions
- Database table schemas
- API endpoint specifications
- Detailed sequence of operations

---

## Key Concepts in System Design

- **Scalability:** Vertical vs Horizontal scaling
- **Distributed Systems:** Replication, Consistency, Availability, Reliability
- **CAP Theorem:** Consistency, Availability, Partition Tolerance
- **Architectures:** Monolithic, SOA, Microservices
- **Load Balancing:** Algorithms (Round Robin, Least Connections, etc.)
- **Databases:** RDBMS (ACID), NoSQL (BASE), Indexing, Partitioning, Sharding
- **Caching:** Mechanisms and strategies
- **Messaging Systems:** Synchronous vs Asynchronous, Pub/Sub, Kafka
- **Performance Metrics:** Latency, Throughput, QPS

---

## Architecture

Architecture in system design refers to the fundamental structures of a software system and the discipline of creating such structures. It defines how system components interact, how data flows, and how the system meets both functional and non-functional requirements.

- **Purpose:** To provide a blueprint for the system, ensuring scalability, reliability, and maintainability.
- **Types:** Monolithic, Microservices, Service-Oriented Architecture (SOA), Event-Driven, etc.

---

## Monolithic Architecture / Centralized Systems

Monolithic architecture is a traditional model where all the components of a system are combined into a single, unified codebase.

- **Characteristics:**
  - Single deployable unit (e.g., one WAR/JAR file or application).
  - All modules (UI, business logic, data access) are tightly coupled.
  - Shared memory and resources.

- **Advantages:**
  - Simple to develop, test, and deploy for small applications.
  - Easier to manage at early stages.
  - Performance can be better due to local calls within the same process.

- **Disadvantages:**
  - Difficult to scale specific components independently.
  - Harder to maintain as the codebase grows.
  - Deployment of any change requires redeploying the entire application.
  - Tight coupling can lead to a "big ball of mud" over time.
  - Single point of failure 

- **Use Cases:** Suitable for small to medium-sized applications with simple requirements and limited scaling needs.

---

## Distributed / Decentralized / Microservices Architecture

### Distributed/Decentralized Architecture

Distributed or decentralized architecture refers to a system where components are located on different networked computers, which communicate and coordinate their actions by passing messages.

- **Characteristics:**
  - Components are distributed across multiple servers or locations.
  - No single point of failure; system can tolerate failures of individual nodes.
  - Data and processing are spread out, improving reliability and scalability.

- **Advantages:**
  - High availability and fault tolerance.
  - Scalability by adding more nodes.
  - Improved performance through parallel processing.

- **Disadvantages:**
  - Increased complexity in communication and data consistency.
  - Harder to debug and monitor.
  - Network latency and partitioning issues.

- **Use Cases:** Large-scale web applications, cloud services, global platforms.

---

### Microservices Architecture

Microservices architecture is an approach where a system is composed of small, independent services that communicate over well-defined APIs.

- **Characteristics:**
  - Each service is independently deployable and scalable.
  - Services are loosely coupled and organized around business capabilities.
  - Technology agnostic—different services can use different programming languages or databases.

- **Advantages:**
  - Enables independent development, deployment, and scaling of services.
  - Fault isolation—failure in one service does not affect others.
  - Easier to adopt new technologies incrementally.

- **Disadvantages:**
  - Increased operational complexity (deployment, monitoring, communication).
  - Requires robust inter-service communication and data consistency strategies.
  - Potential for duplication of effort across services.

- **Use Cases:** Large, complex applications requiring frequent updates, organizations with multiple development teams, cloud-native applications.

---

## What is Latency in Networking?

Latency is the time it takes for data to travel from one point to another in a network. In networking, it usually refers to the delay between sending a data packet and receiving it at the destination. Lower latency means faster response, while higher latency can make systems feel slow.

- **Causes of Latency:**  
  - Physical distance between source and destination
  - Number of routing hops
  - Network congestion
  - Hardware or server processing time

---

## How to Reduce Latency in a Network

1. **Reduce Network Distance:**  
   Place data centers or servers closer to users.
2. **Use Faster Network Devices:**  
   Upgrade to better routers, switches, and cables.
3. **Reduce Network Congestion:**  
   Implement load balancing and traffic management.
4. **Use Caching and CDN:**  
   Store frequently accessed data closer to the user.

---

## What is Throughput?

Throughput is the amount of data, requests, or transactions a system can process in a given amount of time. It is usually measured in "requests per second" (RPS) or "transactions per second" (TPS). Higher throughput means the system can handle more load efficiently.

---

## How to Improve Throughput?

1. **Horizontal Scaling:**  
   Add more servers or nodes to distribute the load.
2. **Load Balancing:**  
   Evenly distribute traffic across all servers.
3. **Optimize Code & Queries:**  
   Improve application code and database queries for faster processing.
4. **Caching:**  
   Store frequently accessed data in cache to reduce repeated computation.
5. **Asynchronous Processing:**  
   Process time-consuming tasks asynchronously or in the background.
6. **Network Optimization:**  
   Reduce network latency and congestion.

---

**Conclusion:**  
To improve throughput, optimize every layer of the system (application, database, network). This allows the system to serve more users efficiently and remain scalable.

---

## What is Availability?

Availability refers to the ability of a system to remain accessible and operational when needed. A highly available system is designed to minimize downtime and ensure that users can access services even in the event of failures.

- **High Availability:**  
  Achieved by eliminating single points of failure and ensuring that the system can quickly recover from faults.

---

### Replication vs Redundancy

#### Replication

- Replication is the process of copying data or services across multiple servers or locations.
- It ensures that if one server fails, another can take over with the same data.
- Common in databases (master-slave, master-master replication) and distributed systems.

**Benefits:**
  - Improves data availability and reliability.
  - Enables load balancing for read operations.

#### Redundancy

- Redundancy means having extra components (hardware, software, or network paths) that are not strictly necessary for normal operation.
- If a primary component fails, the redundant component takes over.

**Benefits:**
  - Prevents single points of failure.
  - Increases system reliability and uptime.

---

**Summary:**  
Both replication and redundancy are strategies to improve system availability. Replication focuses on duplicating data/services, while redundancy provides backup components to handle failures.

---

## What is Consistency in System Design? (Strong vs Eventual Consistency)

Consistency in system design means ensuring that all users see the same data at the same time across a distributed system. It guarantees that after a data update, all nodes reflect the latest value.

### Strong Consistency

- With strong consistency, once data is updated, all users and nodes immediately see the new value.
- Any read operation always returns the most recent (updated) data.
- This is critical for systems like banking or finance, where data accuracy is essential.

### Eventual Consistency

- With eventual consistency, data updates are propagated to all nodes over time.
- For a short period, different users or nodes might see different data, but eventually, all nodes will have the same data.
- This model is suitable for systems like social media or caching, where temporary differences in data are acceptable.

**Summary:**  
Strong consistency provides immediate accuracy but can be slower, while eventual consistency is faster but may show outdated data for a short time.

---

## CAP Theorem In Depth

The **CAP theorem** (also known as Brewer's theorem) states that a distributed data system can only provide two out of the following three guarantees at the same time:

1. **Consistency (C):** Every read receives the most recent write or an error. All nodes see the same data at the same time.
2. **Availability (A):** Every request receives a (non-error) response, even if some nodes are down.
3. **Partition Tolerance (P):** The system continues to operate despite arbitrary network partitions (communication failures between nodes).

### Why Can't We Have All Three?

In a distributed system, network failures (partitions) can happen. When a partition occurs, the system must choose between:
- **Consistency:** Refuse requests that can’t guarantee the latest data (sacrificing availability).
- **Availability:** Serve requests with possibly outdated data (sacrificing consistency).

### Examples

#### 1. CP System (Consistency + Partition Tolerance)
- **Example:** HBase, MongoDB (in some configurations)
- **Behavior:** During a network partition, the system will reject requests that can’t guarantee consistency. Availability is sacrificed.
- **Scenario:** In a banking system, if two branches lose connection, the system may block transactions to prevent inconsistent balances.

#### 2. AP System (Availability + Partition Tolerance)
- **Example:** Couchbase, Cassandra, DynamoDB
- **Behavior:** During a partition, the system continues to accept requests, but some may see stale data. Consistency is sacrificed.
- **Scenario:** In a social media feed, users may see slightly outdated posts during a network issue, but the service remains available.

#### 3. CA System (Consistency + Availability)
- **Example:** Traditional relational databases (not distributed)
- **Behavior:** These systems work well as long as there is no partition. If a partition occurs, the system cannot guarantee both consistency and availability.
- **Scenario:** A single-node SQL database can be both consistent and available, but if the network fails, it cannot tolerate the partition.

### Summary Table

| System Type | Consistency | Availability | Partition Tolerance | Example         |
|-------------|-------------|--------------|---------------------|-----------------|
| CP          | Yes         | No           | Yes                 | HBase           |
| AP          | No          | Yes          | Yes                 | Cassandra       |
| CA          | Yes         | Yes          | No                  | Single-node SQL |

**Conclusion:**  
CAP theorem helps architects understand the trade-offs in distributed systems and choose the right design based on application needs.

---

## What is Lamport Logical Clock in System Design?

A **Lamport Logical Clock** is an algorithm used in distributed systems to order events without relying on synchronized physical clocks. It helps determine the sequence of events (such as message sending and receiving) across different nodes in a distributed system.

### How It Works

- Each process in the system maintains a counter (logical clock).
- When a process performs an event (like sending a message), it increments its counter.
- When a process sends a message, it includes its current clock value.
- When a process receives a message, it sets its clock to the maximum of its own clock and the received clock, then increments it by one.

### Why Use Lamport Logical Clock?

- Physical clocks on different machines can be out of sync.
- Lamport clocks provide a way to establish a partial ordering of events (i.e., which event happened before another).
- Useful for detecting causality and resolving conflicts in distributed databases, distributed transactions, and coordination protocols.

### Example

1. Process A (clock=1) sends a message to Process B.
2. Process B receives the message (its clock=2), compares with the received clock (1), sets its clock to max(2,1)+1=3.
3. This ensures that the event of receiving the message is ordered after the event of sending it.

**Summary:**  
Lamport Logical Clocks help maintain a consistent event order in distributed systems, even when physical clocks are not synchronized.

---

## Difference Between Horizontal and Vertical Scaling

### Horizontal Scaling (Scaling Out)

- **Definition:** Adding more machines or servers to handle increased load.
- **How it works:** Distributes traffic and data across multiple servers.
- **Example:** Adding more web servers behind a load balancer.

**Pros:**
- Increases capacity and fault tolerance.
- No single point of failure—if one server fails, others can take over.
- Easier to scale dynamically in cloud environments.
- Can handle very large workloads.

**Cons:**
- More complex to manage and configure (load balancing, data distribution).
- Requires changes in application architecture to support distributed processing.
- Potential consistency challenges in distributed systems.

---

### Vertical Scaling (Scaling Up)

- **Definition:** Increasing the resources (CPU, RAM, storage) of a single server.
- **How it works:** Upgrades the existing server to handle more load.
- **Example:** Upgrading a server from 8GB RAM to 32GB RAM.

**Pros:**
- Simple to implement—just upgrade the hardware.
- No changes needed in application code or architecture.
- Easier to manage for small-scale systems.

**Cons:**
- Limited by the maximum capacity of a single machine.
- Can become a single point of failure.
- Hardware upgrades can be expensive.
- Downtime may be required during upgrades.

---

**Summary:**  
Horizontal scaling adds more servers for increased capacity and reliability, while vertical scaling upgrades a single server’s resources. Horizontal scaling is better for large, distributed systems, while vertical scaling is simpler but limited in growth.

---

## References

- [System-Design-/README.md](System-Design-/README.md)