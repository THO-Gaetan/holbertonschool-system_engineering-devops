# Web Infrastructure Design

## Project Overview
This repository contains a series of web infrastructure design tasks that demonstrate the evolution of web architectures from simple to complex, distributed systems. Each task includes detailed diagrams created with Mermaid and comprehensive explanations of the infrastructure components, their relationships, and design considerations.

## Project Structure

### Task 0: Simple Web Stack
- **Focus**: Single server setup with web server, application server, and database
- **Concepts**: Basic web hosting, DNS configuration, database management

### Task 1: Distributed Web Infrastructure
- **Focus**: Three-server setup with load balancing
- **Concepts**: Redundancy, load distribution, active-active configuration, database replication

### Task 2: Secured and Monitored Web Infrastructure
- **Focus**: Security enhancements and monitoring implementation
- **Concepts**: Firewalls, HTTPS/SSL, monitoring clients, data collection, security best practices

### Task 3: Scaled Up Web Infrastructure
- **Focus**: Component isolation and clustering
- **Concepts**: Dedicated server roles, high availability, load balancer clustering, scalability

## Learning Objectives
- Design secure and scalable web infrastructures
- Understand network security concepts including firewalls and HTTPS
- Implement high-availability configurations with load balancing
- Configure monitoring systems for performance and security
- Identify and address single points of failure
- Plan for scalability and maintenance requirements

## Technologies
- **Diagramming**: Mermaid for infrastructure visualization
- **Web Server**: Nginx
- **Application Server**: Various (language-agnostic designs)
- **Database**: MySQL with primary-replica configuration
- **Load Balancing**: HAProxy
- **Security**: Firewalls, SSL/TLS
- **Monitoring**: Sumologic (or similar monitoring services)

## Usage
Each task directory contains:
1. A Mermaid diagram file (`.mmd`) visualizing the infrastructure
2. A markdown file (`.md`) explaining the components, design decisions, and limitations

To view the diagrams:
- Use a Mermaid-compatible viewer or editor
- Convert to image formats using Mermaid CLI
- Use online Mermaid editors like Mermaid Live Editor

## Authors
**Gaetan Pineiro :** https://github.com/THO-Gaetan/holbertonschool-system_engineering-devops