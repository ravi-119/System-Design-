## Difference between Redundancy and Replication

### Redundancy

Redundancy is the inclusion of extra components or systems that are not strictly necessary for normal operation, but serve as backups in case of failure.

#### Types of Redundancy

- **Active Redundancy:**  
  All redundant components are running simultaneously and share the load. If one fails, others continue without interruption.  
  *Example:* Multiple power supplies running in parallel.

- **Passive Redundancy:**  
  Backup components remain idle until the primary component fails. When a failure occurs, the backup takes over.  
  *Example:* A standby server that activates only if the main server fails.

---

### Replication

Replication is the process of copying data or services across multiple systems to ensure consistency and availability.

#### Types of Replication

- **Active Replication (Master-Master):**  
  All replicas (nodes) process requests simultaneously and keep data in sync. If one fails, others continue to serve requests.  
  *Example:* Multi-master database replication.

- **Passive Replication (Master-Slave):**  
  One node (master) handles all writes and updates, while one or more nodes (slaves) replicate the data and can serve read requests. If the master fails, a slave can be promoted to master.  
  *Example:* Master-slave database replication.

---

### Summary Table

| Aspect         | Redundancy (Active) | Redundancy (Passive) | Replication (Active) | Replication (Passive) |
|----------------|---------------------|----------------------|----------------------|-----------------------|
| Operation      | All active          | Standby/Idle backup  | All process requests | Only master processes |
| Failover       | Seamless            | Switchover needed    | Seamless             | Switchover needed     |
| Example        | Parallel power units| Standby server       | Multi-master DB      | Master-slave DB       |

---

## Load Balancer

A **load balancer** is a system component that distributes incoming network traffic or application requests across multiple servers to ensure no single server becomes overwhelmed. This improves responsiveness, increases availability, and provides fault tolerance.

### How Load Balancer Works

- Receives incoming client requests.
- Distributes requests to backend servers based on a chosen algorithm.
- Monitors server health and reroutes traffic if a server fails.
- Can operate at different layers (Layer 4 - Transport, Layer 7 - Application).

### Roles of Load Balancer

- **Distributes Traffic:** Spreads incoming requests evenly across servers.
- **Fault Tolerance:** Detects server failures and redirects traffic to healthy servers.
- **Scalability:** Allows addition or removal of servers without downtime.
- **Security:** Can hide internal server details and help mitigate attacks.

### Challenges of Load Balancer

- **Single Point of Failure:** If not designed redundantly, the load balancer itself can fail.
- **Session Persistence:** Maintaining user sessions across multiple servers can be complex.
- **Scalability Limits:** Hardware or software limits may restrict scaling.
- **Latency:** Improper configuration can introduce delays.

### Advantages of Load Balancer

- **High Availability:** Ensures services remain accessible even if some servers fail.
- **Improved Performance:** Distributes load, preventing server overload.
- **Flexibility:** Supports rolling updates and maintenance without downtime.
- **Efficient Resource Utilization:** Maximizes use of all available servers.

### Load Balancing Algorithms

- **Round Robin:** Requests are distributed sequentially to each server.
- **Least Connections:** Sends requests to the server with the fewest active connections.
- **IP Hash:** Uses the client’s IP address to determine which server receives the request.
- **Weighted Round Robin/Least Connections:** Assigns more requests to more powerful servers.
- **Random:** Randomly selects a server for each request.

---






