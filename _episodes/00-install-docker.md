---

title: "Installing Docker"
teaching: Complete before the start of geohackweek
exercises: 3
questions:
- "What do I need to do to prepare for geohackweek?"
- "Do I need to install specific software on my computer?"
objectives:
- "Install Docker on your computer"
- "Test whether Docker is working"
- "Download Docker images for geohackweek"
keypoints:
- "Make sure that Docker successfully runs on your computer so that we can trouble-shoot issues before the start of geohackweek."
- "Download Docker images for geohackweek because the download speeds over wireless are slow especially when 40+ people are trying to download simultaneously."

---

### What is Docker?
 [**Docker**](https://www.docker.com/) wraps software in a complete filesystem which guarantees that the software will run the same in different computing environments.  It works on Linux, OS X and Windows.

 We are using Docker for geohackweek because geospatial analysis depends on many different types of software.  By using Docker, we will be able to create the correct software environments in advance and minimize the amount of software that participants have to install themselves prior to the start of geohackweek.

### Install Docker

1. To install Docker, please click on the link below for your operating system, and follow the instructions on the site**:
  - [Windows](https://docs.docker.com/docker-for-windows/)
  - [OSX](https://docs.docker.com/docker-for-mac/)
  - [Linux](https://docs.docker.com/engine/getstarted/)
2. Once Docker is installed, please follow the instructions in the Getting Started Tutorial for your operating system.

**Docker has specific requirements: Windows and Mac OS X users should read the "Important Notes" and "What to know before you install" sections before installing Docker.  You may need to update your operating system.  Another option is to install [Docker Toolbox](https://www.docker.com/products/docker-toolbox). If you cannot install Docker or Docker Toolbox, please contact geohackweek organizers via the #installdocker Slack channel as soon as possible.

### Open a Command Terminal

### Verify Docker Installation

```bash
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
535020c3e8ad: Pull complete
af340544ed62: Pull complete
Digest: sha256:a68868bfe696c00866942e8f5ca39e3e31b79c1e50feaee4ce5e28df2f051d5c
Status: Downloaded newer image for hello-world:latest

Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker Engine CLI client contacted the Docker Engine daemon.
2. The Docker Engine daemon pulled the "hello-world" image from the Docker Hub.
3. The Docker Engine daemon created a new container from that image which runs the
   executable that produces the output you are currently reading.
4. The Docker Engine daemon streamed that output to the Docker Engine CLI client, which sent it
   to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker Hub account:
https://hub.docker.com

For more examples and ideas, visit:
https://docs.docker.com/userguide/
>>>
```

### Install Docker Images for [geohackweek](https://hub.docker.com/u/geohackweek2016/dashboard/)
