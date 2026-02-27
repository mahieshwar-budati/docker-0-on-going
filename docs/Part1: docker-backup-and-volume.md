# Docker Image & Volume Backup Guide

Author: Mahieshwar Budati

---

# PART 1: Backup a Docker Image

## What is a Docker Image?

A Docker image contains:
- Application code
- Dependencies
- Runtime
- OS layers

Think of it like a blueprint for containers.

---

## Why Backup an Image?

You may want to:

- Move image to another machine
- Store it offline
- Share without Docker Hub
- Create a version snapshot

For this, we use:

docker save

---

## Step 1: List Available Images

```bash
docker images

## Save Image to a Tar File
docker save -o myapp_backup.tar myapp:latest

Explanation:

docker save → Export image

-o → Output file

myapp_backup.tar → File name

myapp:latest → Image reference

Result:

A file is created:
myapp_backup.tar

This file can be:

Stored

Transferred

Uploaded

Archived
