# Why Volume Backup?

###Important Concept:

Docker Image → Application
Docker Volume → Data

Containers are temporary.
Volumes store persistent data.

If:

Server crashes

System migration

Docker reinstall

Volume backup is necessary.

### Step 1: List Volumes
```docker volume ls```

This shows:

DRIVER VOLUME NAME
local myvolume

### Step 2: Backup a Docker Volume

We use a temporary container to access the volume.

```
docker run --rm \
-v myvolume:/volume \
-v $(pwd):/backup \
ubuntu \
tar cvf /backup/volume_backup.tar /volume
```

Deep Explanation

docker run → Start temporary container
--rm → Remove container after finishing
-v myvolume:/volume → Mount Docker volume
-v $(pwd):/backup → Mount current folder
ubuntu → Base image
tar cvf → Create archive file

Result:

volume_backup.tar

Now your volume data is backed up.
