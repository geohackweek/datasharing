---

title: "Introduction to Jupyter & Jupyterhub"
teaching: 10
exercises: 10
questions:
- "What are Jupyter Notebooks?"
- "What is JupyterHub?"
objectives:
- Learn how to share executable code that you've written
---

## Jupyter Notebook

- A Jupyter Notebook App is a web application for running and sharing notebook documents. 
- A notebook document can contain code and other elements that are executable via a kernel. It can also contain rich text and figures.
- A kernel executes the code in a notebook document. A kernel can be an environment (e.g. a conda environment)
- A Jupyter Notebook can help encourage collaboration, and reduces the need to "reinvent the wheel"


## Installing the Single User Jupyter Notebook server


We will use some of the skills learned in the Github tutorial to fork a version of the tutorial contents (https://github.com/geohackweek/tutorial_contents.git) on to your local machine. Then we will use conda to install a sample environment.yml file and run notebooks locally. 

> ## 10 minutes conda and git challenge
>
>  1. Check if you have jupyter notebook installed
>  2. Git fork (https://github.com/geohackweek/tutorial_contents.git) 
>  3. conda install the sample environment file from 
>  4. Launch Jupyter Notebook from inside the git repository
>
{: .challenge}

## What is Jupyterhub 
Jupyterhub: 
- Manages authentication
- Spawns Jupyter Notebook servers on-demand

All notebooks have access to the same set of packages and libraries as specified in the **environment file**.  

Which means...

**Jupyterhub is a way to give a standardized Jupyter Notebook server to each person in a group of people**

![](../fig/geohackweek_aws_setup.png)
## JupyterHub Access
The JupyterHub for GeohackWeek is accessible at: https://jupyterhub.geohackweek.org

You will need a [Github](http://www.github.com) account for authentication. 
