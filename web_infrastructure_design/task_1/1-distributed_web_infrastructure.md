# Distributed Web Infrastructure

## Overview
This document describes a three-server distributed web infrastructure designed to host the website www.foobar.com. This architecture improves reliability and performance through redundancy and load balancing.

## Infrastructure Diagram
The accompanying Mermaid diagram (`1-distributed_web_infrastructure.mmd`) illustrates the complete infrastructure setup with all components and their relationships across three servers.

## Components

### 1. Load Balancer (HAproxy)
- **Purpose**: Distributes incoming traffic across multiple servers
- **Configuration**: Configured with Round Robin algorithm
- **Function**: Improves performance and provides redundancy
- **Benefits**: Prevents server overload and increases availability

### 2. Web Servers (Nginx) - 2 instances
- **Role**: Handle HTTP requests, serve static content
- **Redundancy**: Two separate instances for fault tolerance
- **Configuration**: Each listens on port 80 (HTTP)
- **Function**: Act as reverse proxies to application servers

### 3. Application Servers - 2 instances
- **Purpose**: Execute application code, process dynamic content
- **Distribution**: One instance per server, paired with web servers
- **Functionality**: Handle business logic and data processing
- **Redundancy**: Multiple instances improve reliability

### 4. Application Files (Codebase) - 2 copies
- **Content**: Website code (HTML, CSS, JS, backend code)
- **Deployment**: Identical copies on each application server
- **Management**: Requires synchronization for consistent updates

### 5. Database (MySQL)
- **Primary-Replica (Master-Slave) Cluster**:
  - **Primary Node**: Handles write operations
  - **Replica Node**: Handles read operations, replicates from primary
- **Configuration**: Asynchronous replication
- **Distribution**: Split across separate servers

## Communication Flow
1. User enters www.foobar.com in browser
2. DNS resolution translates domain to load balancer's IP
3. Load balancer receives request and forwards to an available web server
4. Web server forwards request to its paired application server
5. Application server processes request using codebase
6. Database queries executed on appropriate node (read vs. write)
7. Response generated and returned to user through the chain

## Specifics of the Infrastructure

### Load Balancer Algorithm
- **Round Robin**: Requests are distributed sequentially to each server in rotation
- **Characteristics**: Fair distribution, simple implementation
- **Use Case**: Good for servers with similar specifications and capabilities

### Active-Active vs. Active-Passive Setup
- **Current Implementation**: Active-Active
  - All servers actively handle traffic simultaneously
  - Maximum resource utilization
  - Higher throughput capacity
- **Alternative**: Active-Passive would keep servers on standby, only activating during failure

### Database Primary-Replica Cluster
- **Primary Node**: Handles write operations, source of truth
- **Replica Node**: Reads only, provides redundancy and read scaling
- **Replication**: Changes from primary are copied to replica
- **Advantage**: Distributes database load, improves read performance

## Limitations of This Infrastructure
1. **Single Points of Failure (SPOF)**:
   - Load balancer has no redundancy
   - Database primary node has no failover mechanism
   - No redundant network paths

2. **Security Issues**:
   - No firewall implementation
   - No HTTPS encryption
   - Vulnerable to various network attacks

3. **No Monitoring**:
   - No visibility into system performance or issues
   - Difficult to detect failures or performance bottlenecks
   - No proactive alerting for system problems

## Potential Improvements
- Add load balancer redundancy
- Implement firewalls and HTTPS
- Add monitoring and alerting system
- Configure database failover
- Implement content delivery network (CDN)