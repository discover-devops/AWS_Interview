### Properties of Application Load Balancer (ALB)

1. **Layer 7 Load Balancing:**
   - Operates at the application layer (OSI Layer 7), allowing it to make routing decisions based on the content of the request (e.g., URL paths, HTTP headers, HTTP methods).

2. **Content-Based Routing:**
   - Routes traffic based on URL paths, hostnames, HTTP headers, HTTP methods, query string parameters, and source IP address.

3. **SSL Termination:**
   - Supports SSL/TLS termination, allowing the load balancer to decrypt incoming requests and forward unencrypted traffic to the backend servers. Integrates with AWS Certificate Manager (ACM) for managing SSL certificates.

4. **WebSockets and HTTP/2:**
   - Supports WebSockets and HTTP/2, which can improve the performance of web applications.

5. **Sticky Sessions:**
   - Supports sticky sessions (session affinity) by using cookies to ensure that requests from a client are sent to the same backend server.

6. **Health Checks:**
   - Performs health checks on backend targets to ensure traffic is only routed to healthy instances.

7. **Target Groups:**
   - Supports multiple target groups, allowing fine-grained routing and scaling policies for different parts of the application.

8. **Cross-Zone Load Balancing:**
   - Distributes traffic evenly across multiple availability zones.

9. **IP and Instance Target Types:**
   - Can route traffic to EC2 instances, IP addresses, and Lambda functions.

10. **Path-based and Host-based Routing:**
    - Supports routing rules based on the URL path or host headers, allowing different backend services to handle different types of requests.

### Properties of Network Load Balancer (NLB)

1. **Layer 4 Load Balancing:**
   - Operates at the transport layer (OSI Layer 4), making routing decisions based on IP protocol data, such as TCP/UDP ports and IP addresses.

2. **High Performance and Low Latency:**
   - Designed for extreme performance, capable of handling millions of requests per second with ultra-low latency.

3. **Static IP Addresses:**
   - Provides a static IP address for the load balancer, which can be useful for applications that require fixed IP addresses.

4. **TLS Termination:**
   - Supports TLS termination, allowing the load balancer to decrypt incoming requests and forward unencrypted traffic to backend targets. Can also pass-through encrypted traffic.

5. **Cross-Zone Load Balancing:**
   - Distributes traffic evenly across multiple availability zones.

6. **Preserve Source IP:**
   - Preserves the original source IP address of the client, which can be useful for applications that require the client's IP address for processing.

7. **Health Checks:**
   - Performs health checks on backend targets to ensure traffic is only routed to healthy instances.

8. **IP and Instance Target Types:**
   - Can route traffic to EC2 instances, IP addresses, and container instances.

9. **Support for PrivateLink:**
   - Can be used to expose services running inside a VPC to other VPCs or on-premises networks through AWS PrivateLink.

### Differences Between ALB and NLB

| Feature                           | ALB                                      | NLB                                  |
|-----------------------------------|------------------------------------------|--------------------------------------|
| **Layer**                         | Application Layer (Layer 7)              | Transport Layer (Layer 4)            |
| **Routing Based On**              | URL paths, hostnames, headers, methods   | Protocol and port                    |
| **SSL/TLS Termination**           | Yes                                      | Yes (default is pass-through)        |
| **Sticky Sessions**               | Yes                                      | No                                   |
| **WebSockets and HTTP/2**         | Yes                                      | No                                   |
| **Static IP Addresses**           | No (requires Global Accelerator)         | Yes                                  |
| **Preserve Source IP**            | No                                       | Yes                                  |
| **Cross-Zone Load Balancing**     | Yes                                      | Yes                                  |
| **Target Types**                  | EC2 instances, IP addresses, Lambda      | EC2 instances, IP addresses          |
| **Health Checks**                 | Yes                                      | Yes                                  |
| **Performance**                   | Moderate to High                         | Very High, handles spiky traffic     |
| **PrivateLink Support**           | No                                       | Yes                                  |

### When to Use ALB and When to Use NLB

#### When to Use Application Load Balancer (ALB)

- **Content-Based Routing:**
  - If you need to route traffic based on URL paths, hostnames, HTTP headers, or HTTP methods.
- **Web Applications:**
  - Ideal for web applications that require advanced routing, SSL termination, and WebSockets support.
- **Microservices:**
  - Useful for applications following a microservices architecture where different services are exposed under different paths.
- **SSL Offloading:**
  - If you need SSL/TLS termination and want to offload the decryption work from backend servers.
- **Dynamic Scaling:**
  - Suitable for applications that need to scale different parts independently.

#### When to Use Network Load Balancer (NLB)

- **High Performance and Low Latency:**
  - For applications that require extremely high performance and low latency, such as real-time gaming or financial applications.
- **Static IP Requirement:**
  - If you need a static IP address for the load balancer.
- **Preserve Source IP:**
  - If your application needs to see the original source IP of the client.
- **Spiky Traffic:**
  - Can handle spiky traffic patterns better, making it suitable for workloads with unpredictable traffic.
- **Protocol-Specific Routing:**
  - For routing traffic based on protocol and port, such as TCP/UDP.
- **PrivateLink Integration:**
  - When you need to expose services through AWS PrivateLink for secure connectivity between VPCs or on-premises networks.
