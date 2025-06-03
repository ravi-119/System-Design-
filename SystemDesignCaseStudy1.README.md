## Purpose of URL Shortener System

A **URL Shortener** system is designed to convert long, complex URLs into shorter, more manageable links. The primary purpose is to make URLs easier to share, remember, and use, especially in contexts with character limits (such as social media, SMS, or printed materials). Additionally, URL shorteners often provide features like click tracking, analytics, and the ability to customize short links.

### Key Purposes

- **Ease of Sharing:** Short URLs are easier to share in emails, messages, and social media posts.
- **Improved Readability:** Short links are cleaner and more user-friendly.
- **Analytics:** Track the number of clicks, geographic location, and referral sources for each short URL.
- **Redirection:** Redirect users from the short URL to the original long URL seamlessly.
- **Customization:** Allow users to create custom short links for branding or memorability.
- **Resource Management:** Useful for managing and updating links without changing the original content.

**In summary:**  
A URL Shortener system simplifies long URLs, enhances sharing and tracking, and provides valuable analytics and customization features for users and businesses.



### Features ( Length of url, domain )
### Estimates ( Memory, CPU requirements)
### Design goal ( CAP )
### HLD 
### Scaling

---

## Functional Requirements for URL Shortener System

1. **Shorten URL:**  
   Users can submit a long URL and receive a unique, shortened URL.

2. **Redirect to Original URL:**  
   When a user accesses the short URL, the system redirects them to the original long URL.

3. **Custom Short URLs:**  
   Users can optionally specify a custom alias for their short URL (if available).

4. **Analytics and Tracking:**  
   Track and display statistics such as the number of clicks, geographic locations, and referral sources for each short URL.

5. **URL Expiry:**  
   Option to set expiration dates for short URLs (after which they become inactive).

6. **User Accounts (Optional):**  
   Allow users to register, log in, and manage their own short URLs.

7. **API Access:**  
   Provide RESTful APIs for programmatic URL shortening and analytics.

8. **Preview Feature:**  
   Option to preview the destination URL before redirection.

9. **Bulk URL Shortening (Optional):**  
   Allow users to shorten multiple URLs at once.

---

## Non-Functional Requirements for URL Shortener System

1. **Scalability:**  
   The system should handle a large number of URL shortening and redirection requests efficiently.

2. **High Availability:**  
   The service should be available 24/7 with minimal downtime.

3. **Performance:**  
   Redirection should be fast (low latency), ideally under 100ms.

4. **Reliability:**  
   Ensure that shortened URLs always redirect to the correct original URLs.

5. **Security:**  
   - Prevent malicious URLs (phishing, malware) from being shortened.
   - Protect against brute-force attacks on short URLs.
   - Secure user data and analytics.

6. **Data Consistency:**  
   Ensure that URL mappings are consistent and not lost or corrupted.

7. **Fault Tolerance:**  
   The system should continue to function correctly even if some components fail.

8. **Maintainability:**  
   The system should be easy to update, monitor, and debug.

9. **Extensibility:**  
   Easy to add new features (e.g., QR code generation, advanced analytics) in the future.

10. **Compliance:**  
    Adhere to relevant data privacy and protection regulations (e.g., GDPR).

---

## Estimating the System Capacity for URL Shortener

When designing a URL shortener, it’s important to estimate the system’s capacity to ensure it can handle the expected load and data growth. Here are the key aspects to consider:

---

### 1. Traffic Estimates

- **Number of Shortened URLs per Day:**  
  Estimate how many new URLs users will shorten daily (e.g., 10 million/day).

- **Redirection Requests per Second:**  
  Estimate peak and average redirection requests (e.g., 100,000 requests/sec during peak).

---

### 2. Storage Requirements

- **URL Mapping Storage:**  
  Each mapping stores a short URL, original URL, metadata (creation date, user, analytics, etc.).
  - Assume average original URL length: 100 bytes
  - Short URL code: 7 bytes
  - Metadata: 50 bytes
  - **Total per record:** ~160 bytes

- **Annual Storage Calculation:**  
  - URLs per year: 10 million/day × 365 ≈ 3.65 billion
  - Storage per year: 3.65B × 160 bytes ≈ 584 GB/year

---

### 3. Memory and CPU Requirements

- **Memory:**  
  - Frequently accessed mappings (hot URLs) can be cached in memory (e.g., Redis).
  - Estimate cache size based on most popular URLs (e.g., top 1 million URLs × 160 bytes ≈ 160 MB).

- **CPU:**  
  - URL shortening and redirection are lightweight operations.
  - CPU usage mainly depends on encryption (if used), analytics, and API rate limiting.

---

### 4. Bandwidth

- **Redirection:**  
  - Each redirect response is small (HTTP 301/302).
  - Bandwidth depends on the number of requests and response size.

---

### 5. Scaling Considerations

- **Horizontal Scaling:**  
  - Use load balancers and multiple application servers to handle high traffic.
- **Database Sharding:**  
  - Distribute URL mappings across multiple database shards for scalability.

---

**Summary Table**

| Metric                        | Estimate Example                |
|-------------------------------|---------------------------------|
| URLs shortened per day        | 10 million                      |
| Redirection requests per sec  | 100,000 (peak)                  |
| Storage per year              | ~584 GB                         |
| Cache size (hot URLs)         | ~160 MB (1 million URLs)        |
| CPU/Bandwidth                 | Scales with traffic             |

---

**Note:**  
These are rough estimates. Actual requirements depend on expected usage, feature set, and growth projections. Always plan for scalability and monitor real-world usage to adjust capacity as needed.

---

## Design Goals for URL Shortener System

When designing a URL shortener system, it’s important to define clear design goals to guide architectural decisions and trade-offs. The main design goals typically include:

---

### 1. **High Availability**
- The system should be accessible and operational 24/7 with minimal downtime.
- Users should always be able to shorten URLs and access redirections.

### 2. **Scalability**
- The system must handle a large and growing number of URL shortening and redirection requests.
- It should support horizontal scaling to accommodate spikes in traffic.

### 3. **Low Latency**
- Redirection from a short URL to the original URL should be extremely fast (ideally <100ms).
- The user experience should be seamless and instantaneous.

### 4. **Reliability and Consistency**
- Every short URL must reliably redirect to the correct original URL.
- Data consistency should be maintained, especially during updates or failures.

### 5. **Security**
- Prevent abuse (e.g., phishing, malware URLs).
- Protect user data and analytics.
- Implement rate limiting and monitoring to prevent brute-force attacks.

### 6. **Extensibility**
- The architecture should allow for easy addition of new features (e.g., QR code generation, advanced analytics, custom domains).

### 7. **Maintainability**
- The system should be easy to monitor, debug, and update.
- Code and infrastructure should be modular and well-documented.

### 8. **Cost Efficiency**
- Optimize for resource usage to keep operational costs reasonable, especially at scale.

---

**CAP Theorem Consideration:**
- **Consistency:** Ensure users always get the correct redirection.
- **Availability:** The service should always respond to requests.
- **Partition Tolerance:** The system must continue to function even if parts of the network are temporarily unavailable.

*In practice, a URL shortener system typically prioritizes Availability and Partition Tolerance, while aiming for eventual consistency for non-critical operations (like analytics).*

---






## High Level Design (HLD) for URL Shortener System

---

### 1. System Components

- **API Gateway / Load Balancer:** Distributes incoming requests to application servers.
- **Application Servers:** Handle API requests for URL shortening, redirection, analytics, etc.
- **Database:** Stores mappings between short URLs and original URLs, user data, analytics.
- **Cache (e.g., Redis):** Caches hot URL mappings for fast redirection.
- **Analytics Service:** Collects and processes click data.
- **Background Workers:** Handle tasks like analytics aggregation, URL expiration, abuse detection.
- **Admin/Monitoring Tools:** For system health, abuse monitoring, and analytics.

---

### 2. APIs

#### a. Shorten URL
- **Endpoint:** `POST /api/shorten`
- **Request:**  
  ```json
  {
    "original_url": "https://www.example.com/very/long/url",
    "custom_alias": "myalias" // optional
  }
  ```
- **Response:**  
  ```json
  {
    "short_url": "https://sho.rt/abc123"
  }
  ```

#### b. Redirect to Original URL
- **Endpoint:** `GET /{short_code}`
- **Behavior:**  
  - Look up `{short_code}` in cache/database.
  - Redirect (HTTP 301/302) to the original URL.

#### c. Analytics
- **Endpoint:** `GET /api/analytics/{short_code}`
- **Response:**  
  ```json
  {
    "clicks": 1234,
    "unique_visitors": 567,
    "geo_stats": {"US": 1000, "IN": 200, ...},
    "referrers": {"twitter.com": 500, ...}
  }
  ```

#### d. User Management (Optional)
- **Register/Login:** `POST /api/register`, `POST /api/login`
- **User URLs:** `GET /api/user/urls`

#### e. Admin APIs (Optional)
- **Abuse Reports, URL Blacklisting, etc.**

---

### 3. Database Design

#### a. URL Mapping Table

| Field           | Type         | Description                        |
|-----------------|--------------|------------------------------------|
| id              | BIGINT (PK)  | Unique ID (auto-increment or hash) |
| short_code      | VARCHAR(10)  | Unique short URL code              |
| original_url    | TEXT         | The original long URL              |
| user_id         | BIGINT       | (Optional) Owner of the URL        |
| created_at      | DATETIME     | Creation timestamp                 |
| expires_at      | DATETIME     | Expiry timestamp (nullable)        |
| custom_alias    | VARCHAR(20)  | (Optional) Custom alias            |
| is_active       | BOOLEAN      | Active/inactive flag               |

#### b. Analytics Table

| Field           | Type         | Description                        |
|-----------------|--------------|------------------------------------|
| id              | BIGINT (PK)  | Unique ID                          |
| short_code      | VARCHAR(10)  | Associated short code              |
| timestamp       | DATETIME     | Click time                         |
| ip_address      | VARCHAR(45)  | User IP                            |
| referrer        | VARCHAR(255) | Referrer URL                       |
| user_agent      | TEXT         | Browser/device info                |
| geo_location    | VARCHAR(50)  | Country/region                     |

#### c. User Table (Optional)

| Field           | Type         | Description                        |
|-----------------|--------------|------------------------------------|
| id              | BIGINT (PK)  | User ID                            |
| username        | VARCHAR(50)  | Username                           |
| password_hash   | VARCHAR(255) | Hashed password                    |
| email           | VARCHAR(100) | Email address                      |
| created_at      | DATETIME     | Registration date                  |

---

### 4. URL Shortening Algorithm

- **Auto-generated Short Code:**  
  - Use a unique ID (auto-increment or distributed ID generator like Snowflake).
  - Encode the ID using Base62 (characters a-z, A-Z, 0-9) to generate a compact short code.
  - Check for collisions if using custom aliases.

- **Custom Alias:**  
  - If provided, check for uniqueness before saving.

---

### 5. Caching Strategy

- Use Redis or Memcached to cache hot URL mappings.
- On redirect, check cache first; if not found, query the database and update the cache.

---

### 6. Scaling & Reliability

- **Stateless Application Servers:** Can be scaled horizontally.
- **Database Sharding:** Partition URL mappings by short code hash for scalability.
- **Replication:** Use master-slave replication for high availability.
- **CDN:** Serve static assets and APIs globally for low latency.
- **Rate Limiting:** Prevent abuse and brute-force attacks.

---

### 7. Security & Abuse Prevention

- Validate and sanitize all URLs.
- Block known malicious/phishing domains.
- Implement CAPTCHA or rate limiting for anonymous users.
- Monitor for abuse and provide admin tools for blacklisting.

---

### 8. High-Level Architecture Diagram

```
[Client] 
   |
[API Gateway / Load Balancer]
   |
[App Servers] <--> [Cache] <--> [Database]
   |                  |
[Analytics Service]   |
   |                  |
[Background Workers]   |
   |                  |
[Admin/Monitoring Tools]
```

---

**Summary:**  
This HLD covers the main APIs, database schema, core algorithms, caching, scaling, and security considerations for a robust, scalable URL shortener system.



## High-Level Architecture Diagram for URL Shortener System

Below is a simple diagram to visualize the main components and data flow in a scalable URL shortener system:

```
                   +----------------------+
                   |      Clients         |
                   | (Web, Mobile, API)   |
                   +----------+-----------+
                              |
                              v
                   +----------------------+
                   |   Load Balancer /    |
                   |    API Gateway       |
                   +----------+-----------+
                              |
                +-------------+-------------+
                |                           |
        +-------v-------+           +-------v-------+
        | App Server 1  |   ...     | App Server N  |
        +-------+-------+           +-------+-------+
                |                           |
                +-------------+-------------+
                              |
                              v
                   +----------------------+
                   |        Cache         |  (e.g., Redis)
                   +----------+-----------+
                              |
                              v
                   +----------------------+
                   |      Database        |  (Sharded/Replicated)
                   +----------+-----------+
                              |
                              v
                   +----------------------+
                   |   Analytics Service  |
                   +----------------------+

Other Components:
- **Background Workers:** For analytics aggregation, URL expiration, abuse detection.
- **Admin/Monitoring Tools:** For system health, abuse monitoring, and analytics.

```

**Legend:**
- **Clients:** Users or systems making requests to shorten or resolve URLs.
- **Load Balancer/API Gateway:** Distributes requests to available app servers.
- **App Servers:** Handle business logic for shortening, redirecting, and analytics.
- **Cache:** Stores hot URL mappings for fast access.
- **Database:** Stores all URL mappings, user data, and analytics.
- **Analytics Service:** Collects and processes click data.
- **Background Workers:** Handle asynchronous tasks.

---

This architecture supports high availability, scalability, and low latency, and can be extended with additional features as needed.