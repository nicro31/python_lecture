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

## Create your first environment

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

* Creating a new directory. This is readily done using the `mkdir` command

* Creating a new file

