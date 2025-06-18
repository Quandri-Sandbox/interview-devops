## Objective

Simulate a simple orchestration environment:
- Build a Dockerized config service exposing /config
- Run multiple instances locally
- Query them from an orchestrator app that collects config data

## Structure

- `config-service/`: The microservice that returns instance configuration.
- `orchestrator/`: A script to query running config-service containers.
- `services.json`: List of services to query.
  
```
/
├── config-service/
│   ├── app.py                # Placeholder for config service implementation
│   └── Dockerfile            # Placeholder Dockerfile
│
├── orchestrator/
│   └── orchestrator.py       # Placeholder for the orchestrator logic
│
├── services.json             # List of URLs the orchestrator will query
├── README.md                 # Instructions and explanation
```

### config-service/app.py
"""
Create a simple web server exposing GET /config
Returns JSON config built from env vars or a config file.
"""

### config-service/Dockerfile
"""
Create a Dockerfile to containerize the config service
"""

### orchestrator/orchestrator.py
"""
Create a script to query multiple local instances of config-service
Reads URLs from services.json and prints config responses
"""

### services.json
```
[
  "http://localhost:8001",
  "http://localhost:8002",
  "http://localhost:8003"
]
```


## Instructions

1. Build the Docker image for the config service:
   ```bash
   docker build -t config-service ./config-service
   ```

2. Run multiple containers:
   ```bash
   docker run -d -p 8001:8000 -e HOSTNAME=container-A config-service
   docker run -d -p 8002:8000 -e HOSTNAME=container-B config-service
   docker run -d -p 8003:8000 -e HOSTNAME=container-C config-service
   ```

3. Run the orchestrator script:
   ```bash
   python3 orchestrator/orchestrator.py
   ```

## Optional
- Extend to run orchestrator in Docker.
- Mock failures or missing services to test error handling.
- Explain how you'd evolve this into an AWS EC2/SSM version.

---

Good luck! 🚀
