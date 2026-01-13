# Install Python

## Introduction

Python is a high-level programming language released in 1991 by Guido van Rossum, and since then it has become one of the most popular programming languages in the world. In particular, it is really popular among scientists, and it is also often teached as the first contact with programming. Indeed, Python is interesting for several reasons:

  * Open-source, i.e. free, works on all major OS (Windows, Mac, Linux...) 
  * Clear and simple syntax that looks close to natural language
  * Huge amount of libraries that extend the functionnalities of Python, in particular for sciences
  * Great documentation and forum


## Download a Python distribution

Python comes in different **distributions**, which are packaged versions of Python that include the interpreter (what reads and executes the program) along with additional libraries and tools. They are designed for specific use cases, such as Anaconda for data science, CPython as the standard reference implementation, and PyPy for improved performance. These distributions make Python easier to install and use for different needs. For this lecture, we are going to use **Miniconda**, which stands for Minimalist Anaconda.

1. Go to the Anaconda download page: [Anaconda download](https://www.anaconda.com/download)
2. Scroll down to the page bottom, it will look like the following picture, and click on "Download Miniconda Installer"

:::{figure} /images/fig_install_1.png
:align: center
:width: 100%
:::

![](images/fig_install_1.png)

<p align="center">
  <img src="images/fig_install_1.png" style="width:100; height:1000;">
</p>

3. On the next page, select and download the installer corresponding to Miniconda, see figure below

:::{figure} /images/fig_install_2.png
:align: center
:width: 100%
:::

4. When the download is done, open the file and install Miniconda with all the default parameters (you can install the software for your session only if you haven't admin rights on the computer you are using).

## Create your first environment

If the installation ran smoothly, a new application called **Anaconda Prompt** should be available on your Windows session. To find it, just type *Anaconda prompt* in the Windows search bar. Click to open the application, and a small minimalist black window should appear: this is a Windows **terminal** or **console**, see the picture below.

:::{figure} /images/fig_install_3.png
:align: center
:width: 100%

The Windows terminal opened with **Anaconda Prompt**
:::

Before going to Python itself, let us discuss briefly what is the Windows terminal. Basically, this is an interface where you can do everything you would do on Windows with the mouse displacement and click, but instead you need to type text commands. This is thus a bit less intuitive, but it gives you more flexibility and more understanding of what you are doing. The **(base)** text at the top left is specific of the **Anaconda Prompt** and indicates that Python is active.


