## What is a Proxy?

A **proxy** is an intermediary server that sits between a client (such as a web browser) and the destination server (such as a website). When a client makes a request, the proxy forwards the request to the destination server, receives the response, and then sends it back to the client. Proxies are used for various purposes, including security, privacy, content filtering, and performance optimization.

---

## Forward Proxy

**Forward proxy** (often just called "proxy") is a server that acts on behalf of clients, forwarding their requests to the internet or other networks.

### How it Works

- The client sends its request to the forward proxy.
- The proxy evaluates the request, applies any rules (such as filtering or authentication), and forwards it to the destination server.
- The destination server responds to the proxy, which then relays the response back to the client.

### Use Cases

- **Access Control:** Restricting or allowing access to certain websites for users within a network (e.g., in schools or offices).
- **Privacy/Anonymity:** Hiding the client’s IP address from the destination server.
- **Content Filtering:** Blocking access to inappropriate or harmful content.
- **Caching:** Storing frequently accessed resources to improve performance.

### Example

A company uses a forward proxy to control and monitor employee internet usage. When an employee tries to visit a website, the request goes through the proxy, which checks if the site is allowed before forwarding the request.

---

## Reverse Proxy

A **reverse proxy** is a server that sits in front of one or more web servers and handles requests from clients on behalf of those servers.

### How it Works

- The client sends a request to the reverse proxy.
- The reverse proxy forwards the request to the appropriate backend server.
- The backend server responds to the reverse proxy, which then sends the response back to the client.

### Use Cases

- **Load Balancing:** Distributing incoming requests across multiple backend servers to optimize resource use and prevent overload.
- **SSL Termination:** Handling SSL/TLS encryption and decryption, offloading this work from backend servers.
- **Caching:** Storing responses to reduce load on backend servers and improve response times.
- **Security:** Hiding the details of backend servers, protecting them from direct access and attacks.

### Example

A popular website uses a reverse proxy (like Nginx or HAProxy) to distribute incoming traffic among several web servers. The reverse proxy also caches static content and handles HTTPS connections, improving performance and security.

---

## Summary Table

| Proxy Type      | Sits Between         | Main Purpose                  | Example Use Case                  |
|-----------------|---------------------|-------------------------------|-----------------------------------|
| Forward Proxy   | Client & Internet   | Client privacy, filtering     | Office internet access control    |
| Reverse Proxy   | Internet & Servers  | Load balancing, security      | Distributing web traffic, caching |

---

**In summary:**  
A proxy acts as an intermediary in network communication. A forward proxy serves clients and controls outbound requests, while a reverse proxy serves servers and manages inbound requests, providing benefits like load balancing, security, and caching.