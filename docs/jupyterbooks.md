---
fontsize: 18px
mainfont: 'Georgia, serif'
---

# Jupyter Books

This page summarizes one approach to making websites with tables of contents, references, Jupyter Notebooks, and other nice features using [Jupyter Books](https://jupyterbook.org/intro.html). Content is created in `Markdown` (text files) or as Jupyter Notebooks (`*.ipynb` files), and the book will be displayed online as HTML. The result will be a GitHub-based website looking like the Jupyter Books [manual](https://jupyterbook.org/intro.html). 

### Basic references

- Jupyter books documentation starts at [jupyterbook.org](https://jupyterbook.org/intro.html).
- Markdown 1: The "plainest" version of markdown that Jupyter Books understands is [CommonMark](https://commonmark.org/).
- Markdown 2: Jupyter Book supports any Markdown syntx that is upported by Jupyter Notebooks. See details [here](https://jupyterbook.org/file-types/markdown.html).
- Markdown 3: [MyST Markdown](https://jupyterbook.org/content/myst.html) is also understood, which is derived from RMarkdown language used in RStudio.

## 1. Setting up environments and working spaces

### 1.1 Install Jupyter Book
Install via pip (details [here](https://jupyterbook.org/start/overview.html)).: 
```
pip install -U jupyter-book
```

### 1.2 Install ghp-import

The [ghp-import](https://pypi.org/project/ghp-import/) program carries out the posting of a prepared Jupyter Book. This is used after writing content, structuring the table of contents, etc. Install this utility as follows:

```
pip install ghp-import
```

### 1.3 Where to put working and resulting files

Build documentation in a repository OTHER than your `username.github.io/` repo. This documentation repo is where files will be edited, where JupyterBooks will be run to convert to HTML, and where results can be tested on you local computer. 

There should be `README.md` and `LICENSE` files. A `.gitignore` file is recommended to prevent all the HTML and related files being sent when you `push` to GitHub. When satisfied, and local/remote repos are synchronized, [ghp-import](https://pypi.org/project/ghp-import/) is used to send HTML to the website repository (not the same as your documentation repo). 

Make a subfolder called `docs` under the project documentation repo's root and place markdown files, the table of contents and config files there. Place images in a subfolder under `docs` such as `images`. 

To summarize:

1. Write documentation locally using Markdown (possibly including code in `*.ipynb` files) in a repo dedicated to the purpose. Manage GitHub version control normally.
1. Use Jupyter Book command line instructions to generate the HTML and book structure within that local repo.
1. Use `ghp-import` from the root of that local repo to ship web display files to your GitHub `username.github.io` repo.
1. The website is then found using a URL like https://fhmjones.github.io/index.html.

Details follow. 

## 2. Preparing content

Individual pages are written in individual Markdown files. Tables of contents are defined, "code" for including figures, math, references, and other features are described in documentation, first in the [Creat your first book](https://jupyterbook.org/start/your-first-book.html) tutorial, and in more detail under the [Topic Guides](https://jupyterbook.org/basics/organize.html) sections of that documentation.

Non-Markdown content like PDF files, images, etc. need to be managed by keeping them in suitable folders (eg. `\assets`). They will be copied into corresponding locations after building the HTML.

## 3. Building a Jupyter Book

So - you have made all the edits to the Markdown files, images, etc. and you are ready to build and publish the "book". Start in the root folder of your local clone of the documentation repository. 

If you have run builds before, clear the results of previous builds by running the following at the command line:

```
jb clean docs/
```

If jupyter execution is cached, this command will not delete the cached folder. To remove the build folder (including `cached` executables), you can run:

```
jb clean --all docs/
```

Now make the book by running the following command at the command line, in your documentation clone's root directory:

```
jb build docs/
```

IMPORTANT: Non-Markdown content like PDF files, images, etc. need to be copied from source folders (eg. `\assets`) into corresponding locations after building the HTML.

Test results locally by opening the `index.html` file that should be in the `.\docs\_build\html` folder. If all seems ready, the contents of this folder will be copied to your GitHub `username.github.io` website using ghp-import as outlined in the next section. 

## Publishing the Jupyter Book online

Publish to your own `username.github.io` repo so it can be checked by you and seen by others. 

### If target GitHub repo is a personal account 

1. The `ghp-import` utility should have been installed (above).
2. Temporarily set a remote `upstream` location as

   ```
   git remote add upstream https://github.com/username/username.github.io
   ```

3. Send the folder with all HTML and associated materials (images, CSS, etc.) that was generated using `jb build` to the `master` (or `main`) branch at `username.github.io` using the following. Do this on the command line from the folder in which the `docs` folder resides.

   ```
   ghp-import -f --no-jekyll -p -b master docs/_build/html -r upstream
   ```
   Change `master` to `main` depending on the name of your main branch.

4. Stop using that location as this repo's `upstream` by finishing with

    ```
    git remote remove upstream
    ```
    Test results by pointing your browser to `username.github.io`. It may take a short time to update. 

5. Use a `.gitignore` file to avoid synchronizing rendered HTML to a github repo. ALSO, using `jb clean --all \docs` may be wise before `pushing` to github for synchronizing. This may help minimize potential confusion. 

### Version control
If you are using Git to work with branches and synchronize your work to a github account, merge any work done on branches to the `main` branch before carrying out these steps. These instructions have not been tested for pushing edits made on a branch other than `main`. 

Of course, it may be wise to make edits in a new branch, test locally, and merge with `main` before delivering results using `ghp-import` to deliver updates.
    
### If target GitHub repo is an Organization account

The branch of the repository from which a website is displayed is not `master` or `main` but a branch called `docs`. 

As of Oct 19, 2021, the procedure has not yet been tested and documented.

## Parts not yet written

- Writing, and the parts needed for including navigation
- Working with **[jb_tools](https://github.com/eoas-ubc/jb_tools/blob/master/tools_demo/Readme_conda.md)**.
- Markdown for Jupyter books
- Using Jupytext in Jupyter Notebooks to automatically keep both `ipynb` and `md` (and other) versions of your Notebooks.