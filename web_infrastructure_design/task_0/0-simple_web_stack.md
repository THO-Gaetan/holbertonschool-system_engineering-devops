# Simple Web Stack Infrastructure

## Overview
This document describes a one-server web infrastructure designed to host a website accessible via www.foobar.com. The infrastructure uses a single server configuration with all components running on the same machine.

## Infrastructure Diagram
The accompanying Mermaid diagram (`0-simple_web_stack.mmd`) illustrates the complete infrastructure setup with all components and their relationships.

## Components

### 1. Server
- **Physical or virtual machine** hosting all components
- **IP Address**: 8.8.8.8
- **Purpose**: Centralized computing resources for running all services

### 2. Domain Name (foobar.com)
- **Configuration**: www record points to IP 8.8.8.8
- **Function**: Provides human-readable address for website access

### 3. Web Server (Nginx)
- **Role**: Handles HTTP requests, serves static content
- **Configuration**: Listens on port 80 (HTTP)
- **Function**: Acts as reverse proxy to application server

### 4. Application Server
- **Purpose**: Executes application code, processes dynamic content
- **Interaction**: Communicates with web server and database
- **Functionality**: Handles business logic, data processing

### 5 Application Files (Codebase)
- **Content**: Website code (HTML, CSS, JS, backend code)
- **Location**: Stored on server filesystem
- **Deployment**: Accessed by application server to serve content

### 6. Database (MySQL)
- **Type**: Relational database management system
- **Usage**: Stores website data (user information, content)
- **Interaction**: Queried by application server


## Communication Flow
1. User enters www.foobar.com in browser
2. DNS resolution translates domain to IP 8.8.8.8
3. Browser sends HTTP request to server
4. Nginx receives request and forwards to application server
5. Application server processes request using codebase
6. Database queries executed as needed
7. Response generated and returned to user

## Limitations of This Infrastructure
1. **Single Point of Failure (SPOF)**: Entire website goes down if server fails
2. **Downtime During Maintenance**: Updates require taking web server offline
3. **Limited Scalability**: Cannot handle significant traffic increases
4. **No Redundancy**: No backup systems if components fail
5. **Security Concerns**: No firewall or HTTPS implementation

## Potential Improvements
- Add redundant servers
- Implement load balancing
- Configure HTTPS
- Add monitoring
- Separate components onto different servers