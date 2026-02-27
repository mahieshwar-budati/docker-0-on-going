# Docker Container Networking (Frontend + Backend)

Author: Mahieshwar Budati

---

# 1. Introduction to Docker Networking

When multiple containers run separately, they cannot automatically communicate.

Example:
- Frontend (React / UI)
- Backend (Flask / Node API)

If both run in different containers, they need a network to talk to each other.

Docker provides built-in networking.

---

# 2. Bridge Network Concept

Docker default network type = bridge.

A bridge network allows:
- Container-to-container communication
- Internal DNS resolution
- Isolation from host

---

# 3. Create a Custom Bridge Network

```bash
docker network create mynetwork
```
Explanation:

docker network create → creates a new network

mynetwork → custom network name

Check networks:

docker network ls

This lists all Docker networks.

### 6. Run Backend Container
```
docker run -d \
--name backend \
--network mynetwork \
-p 5000:5000 backendimage
```
Explanation:

-d → Run in background (detached mode)

--name backend → Container name

--network mynetwork → Attach to custom network

-p 5000:5000 → Map host port to container port

backendimage → Docker image name

Now backend is running inside mynetwork.

### 5.Run Frontend Container
```
docker run -d \
--name frontend \
--network mynetwork \
-p 3000:3000 frontendimage
```
Explanation:

frontend container also joins the same network

Both containers now share the same internal network

### 6. How Containers Communicate

 Do NOT use inside frontend code:

http://localhost:5000

Why?

Inside a container:

localhost means the container itself

It does NOT refer to backend container

Correct Way

Use container name as hostname:

http://backend:5000

Why this works:

Docker provides internal DNS.
Container name becomes the hostname.

So:

frontend → backend:5000

works perfectly.

### 7. Inspect Network
docker network inspect mynetwork

This shows:

Connected containers

IP addresses

Network configuration

### 8. Remove Network
docker network rm mynetwork

Note:
You must stop containers before removing the network.

### 9. Important Networking Commands

List networks:

docker network ls

Inspect network:

docker network inspect mynetwork

Remove network:

docker network rm mynetwork
### 10. Useful Docker Commands (Bonus Section)
Clean Unused Resources
docker system prune

Removes:

Stopped containers

Unused images

Unused networks

Check disk usage:

docker system df
Inspect Container
docker inspect container_id

Shows detailed JSON configuration.

Copy Files Between Host and Container
docker cp file.txt container_id:/app
Stop All Running Containers
docker stop $(docker ps -q)

Explanation:

docker ps -q → Get all container IDs

docker stop → Stops them


