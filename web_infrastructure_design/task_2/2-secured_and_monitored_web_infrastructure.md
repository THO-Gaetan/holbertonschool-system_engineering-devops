# Secured and Monitored Web Infrastructure

## Overview
This document describes a three-server web infrastructure designed to host the website www.foobar.com with enhanced security, HTTPS encryption, and comprehensive monitoring. This architecture builds upon the distributed model while addressing security concerns and adding observability.

## Infrastructure Diagram
The accompanying Mermaid diagram (`2-secured_and_monitored_web_infrastructure.mmd`) illustrates the complete infrastructure setup with security measures and monitoring systems in place across the three servers.

## Components

### 1. Firewalls (3)
- **Purpose**: Filter network traffic and protect servers from unauthorized access
- **Distribution**: One firewall on each server
- **Function**: Restrict access to only necessary ports and services
- **Benefits**: Prevents malicious traffic and reduces attack surface

### 2. SSL Certificate
- **Purpose**: Enables HTTPS encryption for www.foobar.com
- **Implementation**: Installed on load balancer for SSL termination
- **Function**: Encrypts data in transit between users and web servers
- **Benefits**: Protects user data and privacy, improves security posture

### 3. Monitoring Clients (3)
- **Type**: Data collectors for Sumologic or similar monitoring service
- **Distribution**: One agent on each server
- **Function**: Collect performance metrics, logs, and system data
- **Benefits**: Provides visibility into system health and performance

### 4. Load Balancer (HAproxy)
- **Features**: SSL termination, distribution of encrypted traffic
- **Configuration**: Round Robin algorithm with HTTPS support
- **Security**: Terminates SSL and distributes traffic to backend servers

### 5. Web Servers (Nginx) - 3 instances
- **Security Enhancements**: Runs behind firewalls
- **Monitoring**: Performance and access metrics collection
- **Configuration**: Serves encrypted content through SSL

### 6. Application Servers - 3 instances
- **Protection**: Isolated behind firewalls and web servers
- **Monitoring**: Application performance metrics collection
- **Security**: Access restricted to web servers only

### 7. Database (MySQL)
- **Configuration**: Primary-Replica (Master-Slave) setup
- **Protection**: Firewall-restricted access
- **Monitoring**: Query performance and resource utilization tracking

## Security Measures

### Firewalls
- **Purpose**: Control incoming and outgoing network traffic
- **Implementation**: Network-level protection for each server
- **Configuration**: Allow only necessary protocols and ports
- **Benefits**: Mitigates unauthorized access and potential attacks

### HTTPS
- **Purpose**: Encrypt data transmission between users and the website
- **Implementation**: SSL certificate for www.foobar.com
- **Process**: SSL termination at the load balancer level
- **Benefits**: Prevents data interception and man-in-the-middle attacks

## Monitoring Setup

### Monitoring Clients
- **Data Collection**: System metrics, application logs, network traffic
- **Reporting**: Continuous data transmission to monitoring service
- **Coverage**: All critical components (web server, application server, database)
- **Alerting**: Configured for anomaly detection and threshold breaches

### What is Monitored
- **Web Server**: Request rate, error rates, response times
- **Application Server**: Resource utilization, error logs, application performance
- **Database**: Query performance, replication lag, connection count
- **Network**: Traffic patterns, latency, bandwidth utilization
- **Security**: Failed login attempts, unusual access patterns

## Issues with the Infrastructure

### SSL Termination at Load Balancer
- **Issue**: Decrypted traffic between load balancer and web servers
- **Risk**: Potential for internal network data exposure
- **Mitigation Option**: End-to-end encryption or secure internal network

### Single MySQL Write Server
- **Issue**: Single point of failure for write operations
- **Risk**: Data loss or service disruption if primary database fails
- **Mitigation Option**: Multi-master setup or rapid failover mechanism

### Homogeneous Server Configuration
- **Issue**: All servers have identical components
- **Risk**: Common vulnerabilities across all servers
- **Mitigation Option**: Specialized servers for different functions

## Improvements and Next Steps
- Implement end-to-end encryption
- Add database clustering with automated failover
- Introduce redundant load balancers
- Deploy web application firewalls (WAF)
- Implement content delivery network (CDN)
- Add DDoS protection services