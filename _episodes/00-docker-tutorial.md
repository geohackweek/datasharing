---

title: "Getting Started with Docker"
teaching: 15
exercises: 0
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
These instructions assume that Docker has already been installed on your computer.  If Docker has not been installed, follow these [instructions](https://geohackweek.github.io/preliminary/01-install-docker).

#### Find Docker Images
Existing docker images are available on [Docker Hub](https://hub.docker.com/).

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub1.png)


Enter "geohackweek" in the search box:

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub2.png)


You will see a list of repositories, click on geohackweek2016/vectortutorial:

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub3.png)


To obtain the docker image, copy the Docker Pull Command to use in your terminal:

![Docker Hub](https://raw.githubusercontent.com/geohackweek/Introductory/gh-pages/assets/img/dockertutorial/DockerHub4.png)

#### Docker Hub resources for geospatial research
[geohackweek2016](https://hub.docker.com/u/geohackweek2016/)
[Google Earth Engine](https://hub.docker.com/u/tylere/)
[Anaconda](https://hub.docker.com/u/continuumio/) - The Anaconda Python Distribution.
[Rocker](https://hub.docker.com/u/rocker/) - R and R Studio.

#### Download Docker Images
The `docker pull` command gets the latest version of the docker image from the Docker Hub.
```bash
$ docker pull geohackweek2016/arraystutorial
```
#### View Docker Images
The `docker images` command shows you all the docker images that you have available on your local machine.

```bash
$ docker images
```
#### Create Docker Containers
The `docker run` command starts a new **docker container** using a **docker image**.

A **docker image** is a filesystem and parameters to use at runtime. It doesn’t have state and never changes. A **docker container** is a running instance of an image.

```bash
$ docker run -i -t --name my_container geohackweek2016/arraystutorial
```
The '-i' flag specifies that you want to run the docker container interactively. The '-t' flag specifies that you want run a pseudoterminal when the container is started.  The '--name' flag specifies a name chosen by you for the container.  If you do not use the '--name' flag, then a name will be automatically assigned to the container.

Type `exit` on the command line to leave the docker container.
```bash
root:/# exit
```

#### Start Docker Containers
To view existing docker containers, type `docker ps -a`

```bash
$ docker ps -a
```
The '-a' flag specifies that you want to see all the containers.

To start an existing docker container named 'my_container':
```bash
$ docker start -a -i my_container
```
The '-a' flag specifies that you want to attach the container and the '-i' flag specifies that you want to run the docker container interactively.

To rename a docker container:
```bash
$ docker rename my_container better_name
$ docker ps -a
```

#### Docker Containers work with Jupyter Notebooks

The following command will start a new container with the ports open for jupyter notebooks.
```bash
$ docker run -i -t --name jupyter_container -p 8888:8888 geohackweek2016/arraystutorial
```
The '-p 8888:8888' links the port 8888 on your local filesystem to the port 8888 in the container.

Start a jupyter notebook from the command line of the container.

```bash
root:/#  jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser
```
The '--notebook-dir' flag specifies the folder in the container where the jupyter notebooks are saved.  The '--ip' flag specifies that the port is open for all ip addresses.  The '--port' specifies the port for the browser to find the jupyter notebooks.  The port '8888' must match the ports in the '-p 8888:8888' flag in the `docker run` command.

View the jupyter notebooks by opening an internet browser on your local filesystem and entering the address as http://localhost:8888

#### Deleting Docker Containers and Images

To remove a single docker container:
```bash
$ docker rm my_container
```

To remove all docker containers:
```bash
$ docker rm $(docker ps -a -q)
```
'$(docker ps -a -q)' lists all the container ids which are then removed by the `docker rm` comand.

To remove a single docker image:
```bash
$ docker rmi -f geohackweek2016/arraystutorial
```
The '-f' flag means force the removal of the image which is necessary if an existing docker container was based on the image.  The docker container still functions after the docker image is removed.

#### Linking Data Volumes


- access local data within a docker container

- save data from a docker container to a folder on your local file system


#### Create a Docker Image for Your Project
- create a docker image for your project
- what's in a docker file
- push docker image to docker hub
