Bind-Mounts a file or directory on the host machine is mounted from the host to a container.

This often is convenient in development since every file and/or directory that it's on the container is also easily accessed in the host.

This means that the container has root access to that container meaning that the container can modify file permissions and contents although this can be easily avoided by making the content in a directory read only.

To create a bind mount this easy syntax can be followed

```sh
docker run --mount type=bind,src=<host-path>,dst=<container-path>

or

docker run --volume <host-path>:<container-path>
```

More options for mount can be checked out [in this part](https://docs.docker.com/engine/storage/bind-mounts/) of the official docker documentation.