---

title: "Getting Started with Docker"
teaching: 15
exercises: 15
questions:
- "How to run Docker?"
- "How to create a new Docker image?"
objectives:
- "Explain images and containers"
- "Run a Docker "
- "Restart a Docker container"
-
keypoints:
-
-

---

#### Install Docker
These exercises assume that Docker has already been installed on your computer.  If Docker has not been installed, follow these [instructions](https://geohackweek.github.io/preliminary/01-install-docker).

#### Find Docker Images
Existing docker images are available on [Docker Hub](https://hub.docker.com/).

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub1.png)

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub2.png)

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub3.png)

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub4.png)

#### Download Docker Images
The ```docker pull``` command gets the latest version of the docker image from the Docker Hub.
```bash
$ docker pull geohackweek2016/arraystutorial
```
#### View Docker Images
The ```docker images``` command shows you all the docker images that you have available on your local machine.

```bash
$ docker images
```
#### Create Docker Containers
The ```docker run``` command starts a new **docker container** using a **docker image**.

A **docker image** is a filesystem and parameters to use at runtime. It doesn’t have state and never changes. A **docker container** is a running instance of an image.

```bash
$ docker run -i -t --name my_container geohackweek2016/arraystutorial
```
The '-i' flag specifies that you want to run the docker container interactively. The '-t' flag specifies that you want run a pseudoterminal when the container is started.  The '--name' flag specifies a name chosen by you for the container.  If you do not use the '--name' flag, then a name will be automatically assigned to the container.

Type 'exit' on the command line to close the docker container.


#### Restart Docker Containers
To view existing docker containers, type ```docker ps -a```

```bash
$ docker ps -a
```
The '-a' flag specifies that you want to see all the containers.

To restart an existing docker container named 'my_container':
```bash
$ docker start -a -i my_container
```

To rename a docker container:
```bash
$ docker rename my_container better_name
$ docker ps -a
```

#### Docker Containers work with Jupyter Notebooks
```bash
$ docker run -i -t -p 8883:8883 geohackweek2016/arraystutorial /bin/bash -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8883 --no-browser"
```

- start with jupyter notebooks




- how to view docker containers
- how to start docker containers
- naming docker containers
- deleting docker images
- deleting docker containers


- access local data within a docker container

- create a docker image for your project
- what's in a docker file
- push docker image to docker hub
