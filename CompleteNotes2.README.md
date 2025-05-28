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