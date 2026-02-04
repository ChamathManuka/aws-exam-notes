# AWS Global Accelerator

## Overview
**AWS Global Accelerator (GA)** improves the **availability and performance** of internet-facing applications for a **global audience** by routing traffic over the AWS global network to the closest healthy endpoint.

Global Accelerator operates at **Layer 4 (TCP/UDP)** and uses **static anycast IP addresses**, avoiding DNS caching issues.

---

## Types of Accelerators

### 1. Standard Accelerator
- Improves **availability and latency**
- Routes traffic only to **healthy endpoints**
- Supports **multi-Region failover**
- Uses **health checks**
- Provides **two static anycast IP addresses** per accelerator for high availability
- Most commonly used

### 2. Custom Routing Accelerator
- Designed for **real-time applications**
  - VoIP
  - Gaming
  - Real-time communications
- **No automatic failover**
- **No health checks**
- Requires manual traffic control
- Niche use cases

---

## How Global Accelerator Works
- Uses **anycast IP addresses**
- Same IP is advertised from multiple AWS edge locations
- Routing is done using **BGP**, not DNS
- Clients are automatically routed to the **nearest edge location**
- Traffic is carried over the **AWS global backbone network**
- No client-side DNS resolution or caching involved

---

## Protocol Support
- Supports:
  - **TCP**
  - **UDP**
- HTTP/HTTPS run over TCP:
  - GA **can route** HTTP/HTTPS traffic
  - GA **does NOT terminate or inspect HTTP**
  - TLS termination happens at the ALB or backend

---

## Supported Endpoints
Standard accelerators can route traffic to:
- Network Load Balancers (**most common**)
- Application Load Balancers
- Amazon EC2 instances
- Elastic IP addresses  
Across **one or multiple Regions**

---

## Typical Architecture
Client → Global Accelerator (Anycast IPs)
→ AWS Edge Location
→ AWS Global Network
→ Regional NLB / ALB
→ Backend EC2 / ECS / EKS


- GA is commonly placed **in front of NLB**
- ALB handles all **HTTP/HTTPS logic**
- GA handles **global routing and failover**

---

## Use Cases
- Multi-Region active/active applications
- Global failover
- Gaming (UDP)
- IoT (MQTT)
- Voice over IP (VoIP)
- Latency-sensitive TCP/UDP workloads

---

## GA vs CloudFront

| Feature | Global Accelerator | CloudFront |
|------|------------------|-----------|
| OSI Layer | Layer 4 | Layer 7 |
| Protocols | TCP, UDP | HTTP, HTTPS |
| Static IPs | Yes | No |
| Caching | No | Yes |
| TLS Termination | No | Yes |
| Routing Method | Anycast + BGP | DNS |
| Best For | Non-HTTP, real-time, failover | Web content, APIs, caching |

> **Note:**  
> Global Accelerator uses **AWS edge network locations for Layer-4 routing**,  
> CloudFront uses **CloudFront edge locations for Layer-7 content delivery**.  
> They are **separate services and infrastructures**.

---

## Unicast vs Anycast

### Unicast
- One IP → one physical location
- Traffic always goes to that single endpoint

### Anycast (Global Accelerator)
- Same IP → multiple locations
- Traffic automatically routes to the closest edge

---

## When to Use Global Accelerator
- You need **static IP addresses**
- You need **TCP or UDP support**
- You need **multi-Region failover**
- You want to avoid DNS-based routing delays

## When to Use CloudFront
- You need **web acceleration**
- You need **caching**
- You need **TLS termination**
- You need **Layer 7 features (WAF, headers, cookies)**

---

## ELB vs AWS Global Accelerator

### Elastic Load Balancer (ELB)
- **Regional service**
- Distributes traffic within **one AWS Region**
- Ideal for:
  - EC2
  - ECS
  - EKS backends

### AWS Global Accelerator
- **Global traffic management**
- Routes traffic across **multiple Regions**
- Commonly fronts **regional ELBs**

> **Best Practice:**  
> Use **Global Accelerator → Regional ELB → Backend resources**

---

## Exam Tip
> Choose **AWS Global Accelerator** when the question mentions:
> - Static IPs
> - TCP/UDP workloads
> - Global users
> - Multi-Region failover
> - Low latency without DNS
