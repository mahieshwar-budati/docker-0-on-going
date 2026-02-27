# Docker Image & Volume Backup Guide

## 1. Backup a Docker Image

### Why Backup an Image?

Docker images contain:
- Application code
- Dependencies
- Runtime environment
- OS layers

If you want to:
- Move image to another machine
- Store offline
- Upload to cloud storage
- Share without Docker Hub

You use `docker save`.

---

## Step 1: List Available Images

```bash
docker images

Example output:

REPOSITORY TAG IMAGE ID
myapp latest abc12345
