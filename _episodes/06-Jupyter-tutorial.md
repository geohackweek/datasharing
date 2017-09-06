---

title: "Introduction to JupyterHub"
teaching: 15
exercises: 0
questions:
- "What is JupyterHub?"
objectives:
- learn about our overall computing framework for geohackweek
keypoints:

---

## JupyterHub Access
The JupyterHub for GeohackWeek is accessible at: https://jupyterhub.cloudmaven.org

You will need a [Github](http://www.github.com) account for authentication. 

## Jupyter Notebook

- A Jupyter Notebook App is a web application for running and sharing notebook documents. 
- A notebook document can contain code and other elements that are executable via a kernel. It can also contain rich text and figures.
- A kernel executes the code in a notebook document. A kernel can be an environment (e.g. a conda environment)
- A Jupyter Notebook can help encourage collaboration, and reduces the need to "reinvent the wheel"

## JupyterHub What Is
Here is an amazing slide deck about Jupyterhub: [JupyterHub Thing Explainer](https://www.slideshare.net/willingc/jupyterhub-a-thing-explainer-overview)

If you're lazy, here is one slide: 

![thingexplainer](../fig/jupyterhub_thing_explain.jpg)

## JupyterHub for GeohackWeek

This is a conceptual graphic of our cloud-based JupyterHub environment for geohackweek:

![geohackweek_setup](../fig/geohackweek_aws_setup.png)

- AWS EC2 instance, Github authentication, multiple spawns 
