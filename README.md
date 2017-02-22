# FEC
Python &lt;3 GIS

This course will introduce you to the basic concepts of computer programming in the Python programming language and 


Materials are based on a python-course taught at the Department of Geosciences and Geography, University of Helsinki:

- [Python for geo-people] (https://github.com/Python-for-geo-people/Course-information)
- [Automating GIS-processes] (https://automating-gis-processes.github.io/2016/)

## Course topics

## Lecture notes

## Building the GitHub-pages

This course website has been constructed in a similar way as the full [automating GIS-processes pages](https://github.com/Automating-GIS-processes/2016)
The pages are built using  [Sphinx](http://www.sphinx-doc.org/en/1.4.9/) with modified version of the [Read The Docs theme](http://docs.readthedocs.io/en/latest/theme.html).
Thus you need to install the following pachages in order to modify the pages:

 - Sphinx

    ```
    conda install -c anaconda sphinx=1.5.1
    ```

  - Read The Docs Theme

    ```
    conda install -c anaconda sphinx_rtd_theme=0.1.9
    ```

## .rst files

Sphinx uses .rst -files ([reStucturedText](https://en.wikipedia.org/wiki/ReStructuredText)). and thus the source for the pages need to be written into .rst-files.
Markdown-dokuments `.md` can be converted to `.rst` -format using [Pandoc_convert_md_to_rst.py](Pandoc_convert_md_to_rst) (converts all .md files from the source directory to .rst files).

## building the pages

Shinx pages need to be built into html-format before publishing online.

- If you are starting from scratch, make sure you have a branch `gh-pages`. If not,

`git branch gh-pages` (you only need to do this once!)

## make.bat

- html-pages are built using the make.bat -batchfile:

 `make html` (html-files will be under the docs-folder in the master-branch)
 `make gh-pages` (html-files are generated under the docs-folder in the gh-pages-branch)

- Note! When building site with `make gh-pages` it is necessary to have a folder called `data` with at least a single template file in the root of the repo. Typically you end up having there many files but it is important to have at least a single file there when starting to build your site.

##publish online

- in GitHub, go to [settings](https://github.com/Automating-GIS-processes/FEC/settings)-page of the repo and set the Source for GitHub Pages to gh-pages branch.


