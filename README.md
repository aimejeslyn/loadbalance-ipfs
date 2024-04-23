
## Load Balancing and Reverse Proxy Configuration

This repository contains a Docker Compose setup for configuring an Nginx load balancer and reverse proxy to manage upstream servers for IPFS and IPFS cluster.

### Upstream Servers Configuration

The Nginx configuration defines two upstream server groups:

#### IPFS Upstream Servers (`upstream ipfs`):

- Server 1: `$IP:5001`
- Server 2: `$IP:5001`

#### Cluster Upstream Servers (`upstream cluster`):

- Server 1: `$IP:9094`
- Server 2: `$IP:9094`

### Nginx Server Block Configuration
- Define proxy locations for `/ipfs/` and `/cluster/` paths:
  - Requests to `/ipfs/` are forwarded to the IPFS upstream servers.
  - Requests to `/cluster/` are forwarded to the IPFS cluster upstream servers.
- Provide a default response for other paths, instructing users on how to use the available endpoints.

### Docker Compose Setup
This service exposes port 80 to the host system and mounts configuration files (`/root/loadbalance-ipfs`) and SSL certificates (`/root/ssl`) 
into the Nginx container for customizing the server configurations and enabling HTTPS support.

### Usage
1. Ensure Docker and Docker Compose are installed.
2. Clone this repository.
3. Customize the Nginx configuration (`/root/loadbalance-ipfs/nginx.conf`) according to your requirements.
4. Place your SSL certificates in the `/root/ssl` directory.
5. Run `docker-compose up -d` to start the Nginx container with the configured settings.

