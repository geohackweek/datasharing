---

title: "Introduction to Conda"
teaching: 30
exercises: 10
questions:
- "What is Conda?"
- "Why should I use it?"
objectives:
- explore the benefits of python environments
- discuss how conda can allow you to make the "perfect python environment"
keypoints:
- conda can be installed in two ways (Anaconda and Miniconda)
- this tool will prevent headaches when trying to install packages with dependancies or managing multiple libraries/projects
- projects can be separated by individual environments
- Reproducible environments can be created easily
- Most conda packages are friendly across all platforms
- If you're not convinced about using conda, read [this great blog](http://technicaldiscovery.blogspot.com.br/2013/12/why-i-promote-conda.html)

---
We will start this tutorial by looking at a picture of the perfect python environment.
![Perfect Python Environment](../assets/img/conda/conda-env.jpeg)

> ## Python Environment Discussion
>
> What are the benefits of having a well defined python environment?
>
> [https://etherpad.wikimedia.org/p/geohack-conda](https://etherpad.wikimedia.org/p/geohack-conda)
>
> > ## Solution
> > 1. Avoid future breakage if any dependencies changes
> > 2. Allows better collaboration among team
> > 3. Reliability
> {: .solution}
{: .challenge}

## Ways to create environments and manage packages in Python

1. The most classic is with `pip` as a python package manager, 
along with `virtualenv` as the python environment manager.
2. Next modern classic `pipenv` as a python package and environment manager.
3. What we'll learn, `conda`.

## Review from Preliminary

### What is conda?
- An open source **package** and **environment** management system, 
used by the scientific software community
- From their website: *Package, dependency and environment management for any language—Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, FORTRAN*

### Flavors of conda
- Miniconda:
   
   **Lightweight** distribution of conda; only contains the necessary python packages.

- Anaconda:
 
   A **data science platform** distribution of conda; comes with a lot of scientific python packages.

---
## Exercise: Let's try creating a python environment

Scenerio 1:
Bob is a post-doc. He has been programming in Python for a few years now, 
and he is very comfortable managing his own python environment, 
previously using `pip` and `virtualenv`, but now he's with the "cool" kids using `pipenv`. 
Recently, his studies are shifting more towards a geospatial focus, and he will need python libraries such as gdal, fiona, and netcdf. Let's see what happens.

> ## Bob's adventure
>
> ~~~
> # First bob installs the new pipenv
> pip install pipenv
> 
> # Next he creates a folder for his new geoproject
> mkdir geoproject
> 
> # Next bob creates a requirements.txt using vim text editor so he can share this later
> vi requirements.txt
> 
> # In requirements.txt
> # ipython
> # requests
> # fiona
> # gdal
> # netCDF4
> 
> # Now he installs those packages
> pipenv install -r requirements.txt
>
> # Bob got an error
> ...
> get_dependencies
    legacy_results = self.get_legacy_dependencies(ireq)
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/piptools/repositories/pypi.py", line 335, in get_legacy_dependencies
    self.resolver.resolve(reqset)
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/resolve.py", line 107, in resolve
    self._resolve_one(requirement_set, req)
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/resolve.py", line 264, in _resolve_one
    abstract_dist = self._get_abstract_dist_for(req_to_install)
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/resolve.py", line 214, in _get_abstract_dist_for
    self.require_hashes
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/operations/prepare.py", line 328, in prepare_linked_requirement
    abstract_dist.prep_for_dist(finder, self.build_isolation)
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/operations/prepare.py", line 155, in prep_for_dist
    self.req.run_egg_info()
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/req/req_install.py", line 486, in run_egg_info
    command_desc='python setup.py egg_info')
>  File "/usr/local/lib/python3.6/site-packages/pipenv/patched/notpip/_internal/utils/misc.py", line 698, in call_subprocess
    % (command_desc, proc.returncode, cwd))
> pipenv.patched.notpip._internal.exceptions.InstallationError: Command "python setup.py egg_info" failed with error code 1 in /tmp/tmp_5d7wspdbuild/GDAL/
>
> # Bob looked at https://pypi.org/project/GDAL/, but it's still really confusing to set this up... HELP!
> ~~~
> {: .bash}
{: .challenge}

Scenerio 2:
In the other side of the world, we meet Sandy. She is an advanced undergrad that have attended on of the hackweek at UW eScience. She just started to really program in Python. One of her senior thesis requires her to analyze a geospatial entity. Similar to bob she knows that she will need to use gdal, fiona, and netcdf. Having learned about `conda` in the hackweek she started following the `conda` workflow in creating a new project. Let's see what happens.

> ## Sandy's adventure
>
> ~~~
> # Sandy has installed conda into her linux machine, so her first step now is to make a new directory for the project
> mkdir geoproject
> 
> # Next Sandy creates an environment.yml using vim text editor so she can share this later
> vi environment.yml
> 
> # In environment.yml
> # name: geoproj
> # channels:  
> #   - conda-forge
> # dependencies:
> #   - python=3.6
> #   - ipython
> #   - requests
> #   - fiona
> #   - gdal
> #   - netCDF4
> 
> # Now she installs those packages
> conda env create -f environment.yml
>
> # Sandy suceeded in the install after a few minutes
> Preparing transaction: done
> Verifying transaction: done
> Executing transaction: done
> #
> # To activate this environment, use
> #
> #     $ conda activate geoproj
> #
> # To deactivate an active environment, use
> #
> #     $ conda deactivate
>
> # Sandy activated her new geoproj python environment, and check whether gdal works.
> conda activate geoproj
> gdalinfo --version
> GDAL 2.2.4, released 2018/03/19
> ogr2ogr --version
> GDAL 2.2.4, released 2018/03/19
> ~~~
> {: .bash}
{: .challenge}
---

## So, what's going on? why didn't pipenv work?

- `pipenv` is basically just a nice wrapper that uses `pip` and `virtualenv` under the hood
- `pip` is simply just a python package manager
- `pip` does not handle library dependencies outside of the python packages as well as the python packages themselves
- `pip` wheels can solve some of the lower level dependencies problems that we run into in bob's case, but GDAL Developers did not include these dependencies within the wheels, users have to set it up themselves!

*NOTE: Conda can manage pip packages, but pip cannot manage conda packages*

---
## Concepts of conda

Before start let's ensure that you have conda installed either via Miniconda or Anaconda

~~~
# Check conda version to make sure it's installed.
conda info
~~~
{: .bash}

> ## Conda Help and Manual
>
> To see the full documentation for any command, type the command followed by `--help`. For example, to learn about the conda update command:
>
> ~~~
> $ conda update --help
> ~~~
> {: .bash}
{: .callout}

### 1. Environments

![Conda environments](../assets/img/conda/conda-env2.jpeg)

What is a conda environment?
- Similar to python virtual environments (venv)
- A set of isolated packages in a directory
- Able to be shared via environment files

~~~
# List out available environments
conda env list # The starred * environment is the current activate environment

# Create conda environment from command line (Not Best Practice)
conda create --name myenv --channel conda-forge python=3.6

# Activate conda environment
conda activate myenv

# Deactivate conda environment
conda deactivate

# Create conda environment from environment file (Recommended Best Practice)
conda env create --file environment.yml

# Removing conda environments
conda env remove --yes --name myenv
~~~
{: .bash}

> ## Best practice to share environments
>
> 1. When starting a new environment, always generate it from an environment file rather than the command line.
> 2. As you add packages to the environment, be sure to update the environment file.
> 3. Unless you have to (i.e. Production Environments), try to avoid specifying the version of each package. This will ensure you have the most up to date version that will work across platform.
>
> If you follow these guidelines, you should be able to give your environment file to anyone,
> and they will be able to install your packages with no problem.
{: .callout}

### 2. Channels

![Conda channels](../assets/img/conda/conda-channels.jpeg)

What is a conda channel?
 - Similar to linux repository (or app store)
 - The service is hosted for free at Anaconda Cloud

~~~
# List out your channels and priorities
conda config --get channels

# If you have a few trusted channels that you prefer to use, you can pre-configure these so that everytime you are creating an environment, you won’t need to explicitly declare the channel.
conda config --add channels conda-forge
~~~
{: .bash}

**NOTE: The highest priority channel is where your packages will be installed from no matter if another channel has a higer version!**

**Conda Forge (https://anaconda.org/conda-forge)**

Conda forge is a community led collection of recipes, build infrastructure and distributions for the conda package manager.

Watch Filipe's talk from pycon, one of the conda-forge lead developer, [https://www.youtube.com/watch?v=qJFkIuzD6tI](https://www.youtube.com/watch?v=qJFkIuzD6tI) for more info about how to put your packages into the conda-forge channel!

### 3. Packages

What is a conda package?
- A compiled software package, but when installed also include all of its dependencies even the lower level ones
- Cross platform
- Made from **recipes**

You can search for conda packages at [https://anaconda.org/](https://anaconda.org/) or the terminal shown below.
~~~
# Look at the packages you have installed
conda list

# Let's search for gdal conda
conda search gdal

# Install a single conda package
conda install -c conda-forge gdal

# Or install multiple packages
conda install -c conda-forge gdal fiona

# Removing a conda package
conda remove -n myenv gdal
~~~
{: .bash}

### 4. Recipes

Instruction on how to compile the conda package and its metadata

~~~
package:
  name: pandas
  version: {{ version }}
source:
  url: https://github.com/pydata/pandas/archive/v{{ version }}.tar.gz
  sha256: d9f67bb17f334ad395e01b2339c3756f3e0d0240cb94c094ef711bbfc5c56c80
build:
  number: 0
  script: python setup.py install --single-version-externally-managed --record=record.txt
about:
  home: http://pandas.pydata.org
  license: BSD 3-clause
  summary: 'High-performance, easy-to-use data structures and data analysis tools.'
extra:
  recipe-maintainers:
    - jreback
    - jorisvandenbossche
    - TomAugspurger
~~~
{: .yaml}
---

### For official walkthrough go to [https://conda.io/docs/user-guide/getting-started.html](https://conda.io/docs/user-guide/getting-started.html)
