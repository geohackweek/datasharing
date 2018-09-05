---

title: "Introduction to Jupyter & Jupyterhub"
teaching: 20
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
If you have conda installed, jupyter notebook is also installed by default. Let's try that. We will try to fork a version of  the tutorial contents git repository (https://github.com/geohackweek/tutorial_contents.git)

----- 10 minutes exercise to install your own version of jupyter notebook ----


------



## What is Jupyterhub 
Jupyterhub: 
- Manages authentication
- Spawns Jupyter Notebook servers on-demand

All notebooks have access to the same set of packages and libraries as specified in the **environment file**.  

Which means... 
** Jupyterhub is a way to give a standardized Jupyter Notebook server to each person in a group of people **

## JupyterHub Access
The JupyterHub for GeohackWeek is accessible at: https://jupyterhub.geohackweek.org

You will need a [Github](http://www.github.com) account for authentication. 


   
