# Onion Service Lab

Minimal Docker-based lab that runs a Tor onion service fronted by Nginx with a hardened SSH server.

## Overview

This project is a small, self-contained environment for experimenting with:

- Hosting services over **Tor** as an onion service
- Using **Nginx** as a reverse proxy for the hidden service
- Securing **SSH** access (keys only, no passwords) on a non-standard port

### Services

- **Tor** (`tor/`)
  - Runs a Tor daemon configured as an onion service (see `torrc`)
  - Exposes a hidden service that points to the Nginx container

- **Nginx** (`nginx/`)
  - Serves `index.html`
  - Acts as a reverse proxy for traffic coming from the onion service

- **SSH** (`ssh/`)
  - SSH server listening on port **4242**
  - Root login disabled
  - Password authentication disabled (SSH keys only)

## Usage

1. Build and start the lab:
   - `docker compose up --build`

2. Retrieve the generated onion address from the Tor service logs or hidden service hostname file.

3. Connect via Tor browser or Tor client to access the Nginx-served page.

4. Use SSH with your key pair to connect to the SSH container on port 4242.

> This project is for learning and experimentation only, not for production use.
