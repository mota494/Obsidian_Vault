
## Why use docker

An application depends on more than the source code to run properly, it also relies in dependencies, operating system version, packages, config files and permissions that have to be setup correctly and of course these dependencies works with the rest of the system that isn't not just the application in question.

Docker solves this problems using containers which are isolated groups of processes. Each container has it's own file system that has everything that you want to run like your app and all it's dependencies, system packages and so on.

This might sound like using a virtual machine, and it's not far from the truth.

##### Virtual Machine VS Container

A virtual machine holds a lot of the same benefits as a container, it's isolated from the system and it's easy to reproduce however a virtual machine is way slower than the host and takes a lot more resources because it emulates a whole machine instead. A docker image uses directly the host's resources so the execution speed is much much better.

## Installing Docker

##### Docker Desktop

Just follow the [docker docs](https://docs.docker.com/get-started/get-docker/)

## Starting off

To make sure everything is installed properly run this command on your terminal:

`$ docker run hello-world`

If, for some reason, it says that it doesn't have permission to run just add the user to the docker group with

`$ usermod -aG docker $USER`

## Concepts

- [[Docker Containers]]
- [[Docker Images]]

## Commands

```sh
$ docker image ls # shows images available
$ docker ps # shows the list of active containers
$ docker ps -a # shows the list of every container even the ones that have ended
$ docker logs <NAME> # show the logs of the specified container
$ docker stop <NAME> # stops
$ docker pull <IMAGE> # pulls the image specified
$ docker run <IMAGE> # runs the image specified
$ docker run -p <IMAGE> # specify the port that the container will pass through
$ docker run -d # will run the image detached from the main terminal process
$ docker run --name <NAME> # runs the image with the name specified
$ docker run --rm # container will auto delete after being stopped
$ docker run <NAME>:<VERSION> # will run the image in a specific version
$ docker build -t <IMAGE NAME> . # will build an image based on the Dockerfile
```

## Tags

Tags can be used to specify which version of the image will the container run

For example if we run 

`$ docker run nginx` 

It will run nginx in it's latest release but if we run instead

`$ docker run nginx:1.27`

It will specifically run nginx in the 1.27 version, however this can be dangerous since when the 1.27 version released it can be pointing to the 1.27.0 version but if the developers make a small upgrade and change the default 1.27 to 1.27.1 when run with 1.27 it will run the now default 1.21.1 and not the old 1.27.0, this can be fixed by using digests like this 

`nginx@sha256:062d96d048af5eb484d175d383e65529ead62becaa273ccae3968bf4ee308960`

Digests can be obtained through the command `docker image ls --digests` or through docker hub

## Slim and Alpine versions

Most images by default use a fully featured Debian install, but most images will have a slim version that is much more bare bones versions of Debian. This makes the image much much smaller.

On top of slim versions there will also be some images that will have an Alpine Linux version which is a Linux distro that focuses on being light weight and minimalist.

>[!info]
>Alpine Linux has some differences to debian like not using .deb packages opting for .apk, not coming with bash as the default terminal and having a much much smaller community than Alpine can limit some of it's functionallity

## Persistance

When a container is stopped it's file system and everything done to it is lost, this is fine for most part but for some images like a database, keeping it's data after stopping is a must, for this a mounting type has to be used.

Types of mounting
- [[Bind-Mounts]]
- [[Volumes]]

## Custom images

Through existing docker images the amount of customization is limited to environment variable, arguments, mount files and directories.

Docker makes it easy to create custom images