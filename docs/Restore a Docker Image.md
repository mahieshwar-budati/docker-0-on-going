Restore a Docker Image

If you have a tar file backup:

```docker load -i myapp_backup.tar```

Explanation:

```docker load → Import image```

-i → Input file

After this, run:

```docker images```

The image will appear again.
