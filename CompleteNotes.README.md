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




## References

- [System-Design-/README.md](System-Design-/README.md)