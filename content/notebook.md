# Jupyter Notebooks

## Introduction

So far we have seen two different ways to work with Python, either directly within the Anaconda Prompt or by running a Python script written in a **.py** file. In this section, we are going to discover a third way, calls **Jupyter Notebook**. 

**Jupyter Notebook** is a wrapper around Python that makes possible to work on documents - the notebooks - containing both Python codes and formatted text (most of this course is actually written using Jupyter Notebook). This is very powerful, in particular in the context of data analysis, where you need to dig into the data, try several things, visualize plots, and add text to comment what you are doing and analyze what you see. As a student, the jupyter notebook can be used to write a lab report for instance. As a researcher, it might be used to analyze complex experimental datasets, or prepare figures for publication.

These notebooks are also nice for pedagological objectives, and I advise you to follow this lecture with a notebook opened on the side, so that you can test code and write comments for yourself at the same place; trying to solve the exercise using the notebook is also making things simpler. Finally, they can also be used to share your work with others in a nice formatting, that you can convert to pdf files for instance.

But before you can actually use the **Jupyter Notebooks**, you need to set up a working environment where it is installed.

```{admonition} Exercice
:class: tip
:label: exo_install_notebook
Create a new conda environment called *notebookenv*, with the python version 3.12, and install the **notebook** and **ipywidgets**  libraries (using the `conda install` command, note that you can install several libraries at once by puttinh their name on the same line, separated by space). Using the Anaconda Prompt console, go to the working directory of your choice and create a new directory called *python_notebooks*. Then enter this new directory.

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

As you can see jupyter notebook opens in a web browser (Note that other versions of Jupyter Notebook may look a bit different). The browser is used for its display capabilities but no worries, everything you are doing in the notebook is local to your computer! The main page is basically a file explorer where you will be able to see and open your notebooks. Here I am working in an empty directory, thus nothing shows up. Let's create our first jupyter notebook by clicking on the `New` button and then `Python 3 (ipykernel)` as shown in the figure below.

:::{figure} images/fig_notebook_1_1.png
:align: center
:width: 100%

:::

A new page will open in the browser, with a new fresh (and empty) notebook. The very first thing to do is to save this new notebook, using the `File` menu as shown below.

:::{figure} images/fig_notebook_2_1.png
:align: center
:width: 100%

:::

You can give your notebook any name you like, but avoid spaces and weird characters in the file name. Note also that **it's mandatory to keep the `.ipynb` extension to have a working notebook.** As shown in the figure below, the last time your file was saved is indicated at the top of the notebook: **remember to save your work regularly**. 

:::{figure} images/fig_notebook_3_1.png
:align: center
:width: 100%

:::

Now that everything is up and running, let's write our first line of code! Click on the first cell so that it is active and type any mathematical operation. Then, click on the `Play` button on the toolbar or use `Shift+Enter` to execute the cell (i.e. to run the code).

:::{figure} images/fig_notebook_4_1.png
:align: center
:width: 100%

:::

You should see the result of the code, as well as a number `1` appearing between brackets on the left hand side of the input and output cells, as illustrated below. This number indicates that the cell was run, and in particular that it was the first cell ran.

:::{figure} images/fig_notebook_5_1.png
:align: center
:width: 100%

:::

A new cell was automatically added below the first cell. Try to write any other mathematical operation in this new cell and run it. You should now observe a number `2` on the left hand side of this new cell, like on the figure below, indicating that the cell was run, and in particular that it was the second cell ran in the notebook.

:::{figure} images/fig_notebook_6_1.png
:align: center
:width: 100%

:::

If you click on the first cell of the notebook and run it again, as shown below, you will see now a number `3` on the left hand side, because the cell was run third. It may seem like a small detail, but it is very important. Indeed, the notebook keeps everything you have done in memory, in the order of the cell executions. Therefore, many times the results of a notebook seem unexpected just because the order of the cell execution is not the same as the order of the cell in the notebook: keep it in mind, this will help you to avoid many issues! On the figure below, a toolbar is also highlighted on the right-hand side of the cell. With these buttons you can copy the content of a cell, move it upward or downward in the notebook, create a new cell above or below (keyboard shortcuts `a` and `b`, with the cell selected but not in edition mode), or delete the cell. Sometimes, you might see a star (`*`) appearing in the brackets on the left-hand side of a cell: this means that the cell code is running. If it is longer than expected, and you feel like there might be a bug in your code, you can click the `Stop` button highlighted on the main toolbar at the top of the notebook.

:::{figure} images/fig_notebook_7_1.png
:align: center
:width: 100%

:::

If the `Stop` button is not enough to stop the cell execution, if at some points your notebook appears to bug or freeze, or if you are getting weird results at some point and you don't really get what is happening, try to restart the Kernel using the menu shown below. This will kill the Python interpreter, clean the notebook memory and give you a fresh start: this will save you a lot of frustration in many situations!

:::{figure} images/fig_notebook_8_1.png
:align: center
:width: 100%

:::

Finally, as mentionned in the introduction, a really nice feature of the Jupyter Notebook is the ability to mix Python code and formatted text. To write formatted text, you need to change the "state" of a cell from `Code` to `Markdown`, using the menu of the toolbar shown below. 

:::{figure} images/fig_notebook_9_1.png
:align: center
:width: 100%

:::

Markdown is a lightweight markup language used to format text using simple symbols. It allows you to easily create structured documents (with headings, lists, links, table, etc.) that can possibly be converted into HTML or other formats. Let's write our first Markdown cell with a simple example showing an equation, as illustrated in the figure below.

:::{figure} images/fig_notebook_10.png
:align: center
:width: 100%

:::

Just like for code cells, you actually need to run the cell (with the `Play` button) to observe the result of your Markdown formatting. If everything is ine, you should observe the output shown below.

:::{figure} images/fig_notebook_11.png
:align: center
:width: 100%

:::

Markdown is really powerful, and with a bit of practice you will be able to write documents just as beautiful (or even better) than Word documents. We will not discuss all possible syntaxes of Markdown here, as you will easily find dedicated ressources online. For instance, here is a [Notebook Markdown Cheat Sheet link](https://www.kaggle.com/code/cuecacuela/2025-the-ultimate-markdown-cheat-sheet) I am using quite often to format my documents.

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