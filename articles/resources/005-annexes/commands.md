# Commands — From Zero to Go (SOVD-Lab + Play-with-Docker)

This file collects the exact commands used to build, run, and debug the Go microservice in **SOVD-Lab**.

---

## 1. Build & Run locally

```bash
# Start from project root
docker compose up --build

# Verify health
curl -s http://localhost:8081/healthz
curl -s http://localhost:8081/data/ident/vin

# Inspect logs and containers
docker ps
docker logs <container_id>
docker exec -it <container_id> sh

# Healthcheck debugging
# Check inside container (distroless base image)
ps aux
netstat -tulpn
```

✅ Lesson: healthchecks must run inside the container, not on the host.

```yaml
# Gateway reachability fix
# compose.yaml (fragment)
services:
  gateway:
    ports:
      - "8080:8080"
    command: ["./gateway", "--bind=0.0.0.0:8080"]
```

✅ Lesson: explicit bind to 0.0.0.0 avoids “up but unreachable” issues.

