(content:GetStarted)=
# Install Python

## Introduction

Python is a high-level programming language released in 1991 by Guido van Rossum, and since then it has become one of the most popular programming languages in the world. In particular, it is really popular among scientists, and it is also often teached as the first contact with programming. Indeed, Python is interesting for several reasons:

  * Open-source, i.e. free, works on all major OS (Windows, Mac, Linux...) 
  * Clear and simple syntax that looks close to natural language
  * Huge amount of libraries that extend the functionnalities of Python, in particular for sciences
  * Great documentation and forum


## Download a Python distribution

Python comes in different **distributions**, which are packaged versions of Python that include the interpreter (what reads and executes the program) along with additional libraries and tools. They are designed for specific use cases, such as Anaconda for data science, CPython as the standard reference implementation, and PyPy for improved performance. These distributions make Python easier to install and use for different needs. For this lecture, we are going to use **Miniconda**, which stands for Miniature Anaconda.

1. Go to the Anaconda download page: [Anaconda download](https://www.anaconda.com/download)
2. Scroll down to the page bottom, it will look like the following picture, and click on "Download Miniconda Installer"

:::{figure} images/fig_install_1.png
:align: center
:width: 100%

Screenshot of the bottom of the Anaconda download page
:::

3. On the next page, select and download the installer corresponding to Miniconda, see figure below

:::{figure} images/fig_install_2.png
:align: center
:width: 100%

Screenshot of the Miniconda download
:::

4. When the download is done, open the file and install Miniconda with all the default parameters (you can install the software for your session only if you haven't admin rights on the computer you are using).

## Using the terminal with Anaconda Prompt

If the installation ran smoothly, a new application called **Anaconda Prompt** should be available on your Windows session. To find it, just type *Anaconda prompt* in the Windows search bar. Click to open the application, and a small minimalist black window should appear: this is a Windows **terminal** or **console**, see the picture below.

:::{figure} images/fig_install_3.png
:align: center
:width: 100%

The Windows terminal opened with **Anaconda Prompt**
:::

Before going to Python itself, let us discuss briefly what is the Windows terminal. Basically, this is an interface where you can do everything you would do on Windows with the mouse displacement and click, but instead you need to type text commands. This is thus a bit less intuitive, but it gives you more flexibility and more understanding of what you are doing. The **(base)** text at the top left is specific of the **Anaconda Prompt** and indicates that Python is available in this terminal.

The other piece of text, `C:\Users\318234>` indicates the **working directory** (or folder if you prefer) where the terminal is open. It can be visualize with the Windows Explorer:

:::{figure} images/fig_nav_directory_1.png
:align: center
:width: 100%

The same working directory opened in the Windows Explorer
:::

Just like you would navigate through your directories using the mouse and click, you can navigate the directories within the terminal. For instance to enter a subdirectory that is in the current working directory, such as the *Documents* directory on the picture above, use `cd` followed by the subdirectory name and press Enter.

:::{figure} images/fig_nav_directory_2.png
:align: center
:width: 100%

Entering a subdirectory in the current working directory
:::

You can navigate back by using the `cd..` command in order to go up one level in the directory tree.

:::{figure} images/fig_nav_directory_3.png
:align: center
:width: 100%

Going up one level
:::

When you navigate through the folder hierarchy, you can also move across multiple directories at once.


:::{figure} images/fig_nav_directory_4.png
:align: center
:width: 100%

Moving across multiple directories
:::

And if you know the full path of your directory, from the root directory `C:`, you can even access it directly, no matter is the current directory you are working in.

:::{figure} images/fig_nav_directory_5.png
:align: center
:width: 100%

Access a directory with the full path
:::

It is fun to navigate to the directory of our choice, but at some point we would like to see what is actually in the directories, just like we see folder icons in the Windows Explorer! This is achieved using the `dir` command.

:::{figure} images/fig_nav_directory_6.png
:align: center
:width: 100%

Looking at directory content within the terminal
:::

Here is the equivalent view using the Windows Explorer:


:::{figure} images/fig_nav_directory_7.png
:align: center
:width: 100%

Windows Explorer view of the directory content
:::

That's it, you know how to navigate into your computer using the terminal! 👍 Now, we would like to be able to interact and modify the files located on the computer, right? Actually, for this lecture we need to be able to do only two things:

* Creating a new directory. This is readily done using the `mkdir` command.

:::{figure} images/fig_nav_directory_8.png
:align: center
:width: 100%

Creating a new directory and going in
:::

* Creating a new text file. We can do that by calling (in the terminal) any basic text editor already installed on Windows, followed by the name of the new file. It is very important to explicitely write the **file extension**! In this lecture, you will need to create Python files with the extension **.py** (even though they are nothing else than simple text file at the end).

:::{figure} images/fig_nav_directory_9.png
:align: center
:width: 100%

Creating a Python file using the Windows notepad application
:::

Even though you can edit this file with any text editor, I advise you to use an **Integrated Development Editor (IDE)**. This is basically a text editor specialized for code writing, with automatic syntax recognition and auto-completion among others. PyCharm is a good choice for Python. If it is not installed on your computer just follow [this link](https://www.jetbrains.com/pycharm/download/?section=windows) to download and install the program, there is a free version. Once PyCharm is installed and you double-click the .py file in the Windows Explorer, Windows should automatically open the file in PyCharm. You will see a screen as shown below:

:::{figure} images/fig_pycharm_light_edit.png
:align: center
:width: 100%

Opening a Python file .py with PyCharm
:::

PyCharm is asking if you want to open the file in *light edit* or in *project*. Project mode gives access to many additionnal functionnalities to set up your Python environment. In this lecture, we are going to do so using the terminal, therefore we will only use the *light edit* mode. You can close the file for now, we will come back to it the next section.

## Creating your first environment

Now that you master the file manipulation with the terminal, let's go back to the Python part of the Anaconda Prompt ! Below is again the Anaconda Prompt terminal when you open it:

:::{figure} images/fig_install_3.png
:align: center
:width: 100%

The Anaconda Prompt terminal
:::

Besides the current directory, you have noticed the `(base)` text on the top left. This text indicates that there is currently a **Python environment** loaded and available in this terminal, the **base** environment. It means that you can launch a Python interpreter: type `python` and press enter:

:::{figure} images/fig_python_interpreter_terminal.png
:align: center
:width: 100%

The Python interpreter opened in the terminal
:::

When the interpreter open, you will see several information related to your installation of Python. First, `Python 3.13.9` refers to the version of Python installed. These versions correspond to the time evolution of Python since its creation, just like Windows had several versions (95, NT, XP, Vista, 7, 8, 10, 11...), with some functionnalies removed and some others added. In general it is a good idea to use the last Python version, but for this lecture we are going to stick with Python version 3.12 in order to be sure that we are all using the same tools!  Then you see that it is indicated that we are using the Python distribution provided by Anaconda, with some more information afterwards.

Finally, on the last line there are now three chevrons `>>>`: it indicates that the interpreter is waiting for some Python code. You can write any Python code here, and press Enter. The interpreter will read your code and execute it. For instance, let's try to perform a simple multiplication as shown below:

:::{figure} images/fig_python_terminal_multiplication.png
:align: center
:width: 100%

A simple multiplication performed using Python in the terminal
:::

That's it, you have executed your first Python code! In principle one could write any program here, but using the terminal is really not convenient when writing long code with many lines: in practice, we will never use this Python console in this lecture. Shut down the Python interpreter using the `exit()` command followed by pressiong Enter, as shown below:

:::{figure} images/fig_python_terminal_exit.png
:align: center
:width: 100%

Shutting down the Python interpreter
:::

As you can see, performing basic operations with Python is really straightforward. And actually, this is what Python basically does: basic mathematical operations such as +, -, x, /. Fortunately, based on these people have built more elaborated tools that can perform much more complex calculations. These tools are called **libraries**, but you will learn about them much lately in the lecture. For now, just keep in mind that a library is a tool that will help you to solve a specific set of problems. 

I told you previously that the `(base)` text in the terminal was indicating that a Python environment was available. You can think of an environment as a toolbox, that you will fill with the tools you need to solve the problem your program is designed to address. In real life, if you need to do some plumbing or mechanical work, you will fill your toolbox with different tools as illustrated below. 

:::{figure} images/fig_toolbox.png
:align: center
:width: 100%

Python environments are just toolboxes, that you will fill with the tools you need for a specific problem
:::

This is just the same with Python. For every problem you need to solve, you will use a new toolbox, i.e. **a new Python environment**, that you will fill with the tools you need, which are libraries in Python. The tools contained in a Python environment can be listed using the `conda list` command. This command will list all tools (i.e. libraries) available in the active environment (the one with the name written between parenthesis on the terminal). For instance the figure below shows the tools in the `(base)` environment:

:::{figure} images/fig_base_conda_list.png
:align: center
:width: 100%

Librairies available in the base environment
:::

As you can see, the `base` environment already contains some libraries even though we haven't done anything special yet. These are simple libraries required for the basic functioning of Python. Now, if you want to build a Python program to solve a particular problem, you are going to create a new toolbox, i.e. environment, that you will then fill with tools. Creating a new Python environment can be done using the `conda create` command. This command expects a name for the environment, specified by the `-n name` command, where `name` can be any name you want to give to the environment (without spaces or any weird characters such as accents!). It is also possible to specify the Python version we want to use for the environment. As stated previously, in this lecture we are going to use Python 3.12, which can be specificied using the `python=3.12` option. All together, here is the full command to create the new environment:

:::{figure} images/fig_create_new_env.png
:align: center
:width: 100%

Creating a new Python environment
:::

At some point, the terminal will ask you if you really want to create the environment, as shown below:

:::{figure} images/fig_confirm_new_env.png
:align: center
:width: 100%

Python is asking for a confirmation before creating the new environment
:::

Just type `y` and press Enter. Note that even before that Python may ask you if you accept the Terms of Service; if so just press the right letter to accept and press Enter. If everything works properly, you should end up with the following message in the terminal:

:::{figure} images/fig_create_done.png
:align: center
:width: 100%

The terminal after the successful creation of a new Python environment
:::

