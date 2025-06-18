Volumes are much more safe and appropriate for a production environment, outside of the testing phase. This type of mounts are managed by the docker daemon and not depend on the hosts file system, making it safer since the container does not need access to the host file system, this makes it possible and easier to share across multiple containers.

Volumes can use remote or cloud storage units like AWS EFS, NFS, SSHFS, etc...

To create a volume you can use this:

```sh
 docker run --mount type=volume,src=<volume-name>,dst=<mount-path>

or

 docker run --volume <volume-name>:<mount-path>
```

More options can be found on the [official docker documentation](https://docs.docker.com/engine/storage/volumes/) page