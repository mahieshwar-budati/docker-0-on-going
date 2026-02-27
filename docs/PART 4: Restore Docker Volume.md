PART 4: Restore Docker Volume

To restore:

```
docker run --rm \
-v myvolume:/volume \
-v $(pwd):/backup \
ubuntu \
bash -c "cd /volume && tar xvf /backup/volume_backup.tar --strip 1"
```

Explanation:

Extract backup into volume

--strip 1 removes root directory layer

Now data is restored inside the volume.
