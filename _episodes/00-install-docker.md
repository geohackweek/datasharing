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

 We are using Docker for geohackweek because geospatial analysis depends on many different types of software.  By using Docker, we will be able to create the correct software environments in advance while minimizing the amount of software that participants have to install themselves prior to the start of geohackweek.

### Installing Docker

1. To install Docker, please click on the link below for your operating system, and follow the instructions on the site:
  - [Windows](https://www.docker.com/products/docker#/windows)
  - [OSX](https://www.docker.com/products/docker#/mac)
  - [Linux](https://www.docker.com/products/docker#/linux)
2. Once Docker is installed, please follow the instructions in the Getting Started Tutorial for your operating system.  

**Anaconda**:

```bash
$ python
Python 2.7.11 |Anaconda custom (x86_64)| (default, Dec  6 2015, 18:57:58)
[GCC 4.2.1 (Apple Inc. build 5577)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
Anaconda is brought to you by Continuum Analytics.
Please check out: http://continuum.io/thanks and https://anaconda.org
>>>
```

### Installing Miniconda

##### Windows
Navigate to http://conda.pydata.org/miniconda.html and download the proper installer for you Windows platform (32 or 64 bits).
We recommend to download the Python 2 version of Miniconda as not all packages are Python 3-compliant yet.  You can still create new Python 3 environments using the Python 2 verson of Miniconda, so you are not limiting yourself.

When installing you will be asked if you wish to make the Anaconda Python your default Python for Windows.
If you do not have any other installation that is a good option.  If you want to keep multiple versions of python on your machine (e.g. ESRI-supplied python, or both 32 and 64 bit versions of Anaconda), then don't select the option to modify your path or modify your windows registry settings.

##### Linux and OSX
You may follow manual steps from http://conda.pydata.org/miniconda.html similar to the instructions on Windows (see above). Alternatively, you can execute these commands on a terminal shell (in this case, the bash shell):

```bash
url=http://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
curl $url -o miniconda.sh
bash miniconda.sh -b
export PATH=$HOME/miniconda2/bin:$PATH
conda update --yes --all
```

### Using Conda to manage packages and create environment
The full list of commands for `conda` is listed within `$ conda --help`

- Using `conda`, you can create an *environment* for your project. An environment is a set of packages that can be used in one or multiple projects. The default environment with Anaconda is the root environment, which contains Anaconda default packages listed [here](https://docs.continuum.io/anaconda/pkg-docs)

  - **Creating an environment**

    An environment can be created in two ways:

    1. An environment file in YAML format (`environment.yml`)

      To install the environment, `myenvironment`:

      ``` bash
      $ conda env create --file environment.yml
      ```

    2. Manual specifications of packages
      To create an environment called `test_env` with packages `numpy`, `matplotlib`, and `pandas` with `python=2.7` from the `conda-forge` channel:

      ``` bash
      $ conda create -c conda-forge -n test_env python=2.7 numpy matplotlib pandas
      ```

  - **Using an environment**

    To activate `test_env` environment:

    **OSX and Linux**

    ``` bash
    $ source activate test_env
    ```

    **Windows**

    ``` bash
    $ activate test_env
    ```

    To deactivate `test_env` environment:

    **OSX and Linux**

    ``` bash
    $ source deactivate
    ```
    **Windows**

    ``` bash
    $ deactivate
    ```

    To verify an environment:

    ``` bash
    $ conda info --envs
    ```

    The current environment is indicated by (\*) character

  - **Listing available environments**

    To list the environments available to be used:

    ``` bash
    $ conda env list
    ```

  - **Listing available packages in an environment**

    To list the packages available to be used in an environment:

    ``` bash
    $ conda list
    ```

  - **Removing and environment**

    To remove the `test_env` environment, you have to first deactivate the environment and then type:

    ``` bash
    $ conda remove -n test_env --all
    ```

  Note: For further commands about managing an environment go to link [here](http://conda.pydata.org/docs/using/envs.html)
