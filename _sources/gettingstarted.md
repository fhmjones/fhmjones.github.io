# Getting Started

## The Goal

These guidelines will help you to set up your local computer from scratch, so that you can start "`The Jupyter Notebook`" facility from the command line, then run or edit code or comments in any `*.ipynb` file. Working with othe file types such as Python(`*.py` files), markdown (`*.md` files), or others will be discussed elsewhere.

## The sequence of steps 

1. Be sure you can navigate your computer's folders using PowerShell (on windows) or Bash (on Mac).
2. Install the open-source package-management system and environment-management system called `miniconda`.
3. Install the Jupyter software.
4. Run the Jupyter Notebook program to edit and execute "Jupter Notebooks" in your default browser.

Details follow.

## 1. Your command shell

If you are not familiar with using a shell or command-line interface, a good place to start is our [Command line and Shells](https://fhmjones.github.io/commandline.html) page. Or - a more conversational introduction is in our "crash course" page called [Powershell and System Administration Crash Course](shells_crash_course.md).

In windows, 

## 2. Installing miniconda

The open-source package-management system and environment-management system we use is `miniconda`. Its purpose is outlined at the conda documentation site [here](https://conda.io/projects/conda/en/latest/index.html).

1. Install by choosing the Windows or macOS instructions under "Regular installation" at the Conda website [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html#regular-installation). Choose the Python 3.9 version, 64-bit (bash if on macOS).
2. Windows: To complete the "[Verify your installer hashes](https://conda.io/projects/conda/en/latest/user-guide/install/download.html#hash-verification)" step, open the Windows "Start" menu and type "Powershell". Then navigate (use `cd` to change directory, `ls` to list the folder contents, etc ... ) to the download folder where your miniconda executable file will be waiting, and type 
    ```
    Get-FileHash filename -Algorithm SHA256
    ```
    Compare the resulting very long string to that next to the link you used to download the package (it is [here](https://docs.conda.io/en/latest/miniconda.html)).

    Then finish the [instruction steps](https://conda.io/projects/conda/en/latest/user-guide/install/windows.html) starting at "Double-click the `.exe` file".

3. macOS: These instructions need to be added ...

If you're new to the conda "environment manager", a quite comprehensive introduction is at [A guide to conda environments](https://towardsdatascience.com/a-guide-to-conda-environments-bc6180fc533).

## 3. Getting started with Jupyter Notebook 

Jupyter software is easily installed following directions under the heading **Getting Started with Classic Jupyter Notebook** on the [Jupyter installation](https://jupyter.org/install.html) page. Do NOT bother installing JupyterLab at this stage.

## 4. Using Jupyter Notebook for the first time.
A well-paced tutorial from August 2020 is [How to Use Jupyter Notebook in 2020: A Beginner’s Tutorial](https://www.dataquest.io/blog/jupyter-notebook-tutorial/). HOWEVER, assuming you have carried out steps 1-3 above (or their equivalent), ignore the **Installation** section. 

The introduction to using Jupyter notebooks starts at **Creating Your First Notebook** and goes to the section "**Example Analysis**".

After that, the tutorial becomes more of a "python" tutorial. It is quite good and worthwhile if you are new to Python. The third section called "**Sharing Your Notebooks**" introduces you to GitHub - again, it is well done, and worthwhile if you are new to using GitHub. *(Note: this tutorial is online, but apparently not "opensource". We may want to find one that has a Creative Commons license, so we can clone it and take charge of it for future maintenance purposes.)*
