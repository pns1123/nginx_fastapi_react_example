## Prerequisites
A working [Docker installation](https://docs.docker.com/engine/install/) (tested with Docker Engine version 26.1.1) is required.

## Getting Started

Start the application by running
```
docker compose up
```
Once the services are running, the website is available on http://localhost:8090/.

## Overview
- NGINX serves as a reverse proxy
- requests to /api are routed to the backend and rewritten so that the /api prefix is dropped:
  -  /api/   =>   /
  -  /api/foo   =>   /foo
  -  ...
- Frontend and Backend service ports do not need to be exposed to the host because the reverse proxy service sends the requests through the Docker network

```
                                      ┌──────────────────┐     
                            ┌────────►│ Frontend (React) │     
                            │         └──────────────────┘         
┌──────┐      ┌───────┐     │                                  
│ User ├─────►│ NGINX ├─────┤                                  
└──────┘      └───────┘     │                                  
                            │  /api   ┌───────────────────────┐
                            └────────►│ Backend API (FastAPI) │
                                      └───────────────────────┘
```

## TODO
- add a workflow to deploy the site to a VM
                                                               
                                                               
                                                               
                                                               
                                                               
                                                               
                                                               
                                                               

