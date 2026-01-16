# Jupyter Notebooks

## Introduction

So far we have seen two different ways to work with Python, either directly within the Anaconda Prompt or by running a Python script written in a **.py** file. In this section, we are going to discover a third way, calls **Jupyter Notebook**. 

**Jupyter Notebook** is a wrapper around Python that makes possible to work on documents - the notebooks - containing both Python codes and formatted text. This is very powerful, in particular in the context of data analysis, where you need to dig into the data, try several things, visualize plots, and add text to comment what you are doing and analyze what you see.

These notebooks are also nice for pedagological objectives, and you will use them a lot to learn about Python. Finally, they can also be used to share your work with others in a nice formatting, that you can convert to pdf files for instance.

But before you can actually use the **Jupyter Notebooks**, you need to set up a working environment where it is installed.

```{admonition} Exercice
:class: tip
:label: exo_install_notebook
Create a new conda environment called *notebookenv*, with the python version 3.12, and install the **notebook** and **ipywidgets**  libraries. Using the Anaconda Prompt console, go to the working directory of your choice and create a new directory called *python_notebooks*. Then enter this new directory.

To check your installation, type the following command in the terminal and press Enter: `jupyter notebook`. If everything ran smoothly, a page should open in your web browser, with some kind of file explorer displayed. If not, try again ! 😉
```

```{dropdown} Solution
Here are the step to set up your environment with notebooks installed:

- Create the new environment

:::{figure} images/fig_create_env_notebook.png
:align: center
:width: 100%

:::

- Do not forget to activate this new environment!

:::{figure} images/fig_activate_env_notebook.png
:align: center
:width: 100%

:::

- Install the *notebook* and *ipywidgets* packages

:::{figure} images/fig_install_notebook_ipywidgets.png
:align: center
:width: 100%

:::

- Go the working directory of your choice, create a new directory called *python_notebooks* and go inside

:::{figure} images/fig_go_working_dir.png
:align: center
:width: 100%

:::

- Now type `jupyter notebook` in the terminal and press Enter, you should obtain a window like this one:

:::{figure} images/fig_open_jupyter_notebook.png
:align: center
:width: 100%

:::

```

## Notebook functionnalities

Under construction...

[Notebook Markdown Cheat Sheet](https://www.kaggle.com/code/cuecacuela/2025-the-ultimate-markdown-cheat-sheet)

```{admonition} Exercice
:class: tip
:label: exo_reproduce_notebook
Try to reproduce the following notebook using the Markdown Cheat Sheet

:::{figure} images/fig_reproduce_notebook.png
:align: center
:width: 100%

:::

```

```{dropdown} Solution

:::{figure} images/fig_reproduce_notebook_solution.png
:align: center
:width: 100%

:::
```