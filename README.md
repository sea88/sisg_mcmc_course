SISG MCMC COURSE
================
30 June, 2017

-   [GETTING AND COMPILING THE LECTURES](#getting-and-compiling-the-lectures)
-   [ADDING R CODE COMPANIONS](#adding-r-code-companions)
-   [LICENSE](#license)

<!-- README.md is generated from README.Rmd. Please edit that file -->
This repository includes the LaTeX source code and the image files to produce the lectures used by Eric C. Anderson and Matthew Stephens in their course "Markov Chain Monte Carlo for Statistical Genetics" taught at the Summer Institute in Statistical Genetics (SISG).

It also includes some recently added "R code companions" to the lectures.

These lecture notes were originally written by Eric C. Anderson and Mike Denham in the spring of 2004 for the SISG that was taught that year at North Carolina State University. The pair taught the same course in 2005. After that, Matthew Stephens took over Mike Denham's part of the course, adding lectures and rewriting significant portions of others.

We are grateful to Mike Denham for providing the style files for formatting the lectures. These files begin with "mcd".

This repository was initialized on GitHub in 2014. It does not include the revision history over the previous 5 years (when it was under version control with subversion).

GETTING AND COMPILING THE LECTURES
----------------------------------

Each lecture or section of the course is compiled as its own LaTeX document, and the PDFs are catenated afterward. The script `./lectures/PDFLatexThem.sh` runs LaTeX twice on each lecture/section of the course. The script `./lectures/CatenatePDFs.sh` catenates the PDFs together. Note that this relies on a Mac-specific script.

Here are the basic directions:

``` sh
# get the repository:
git clone ...

# change into the lectures directory
cd ./sisg_mcmc_course/lectures

# typeset it all
./PDFLatexThem.sh

# catenate the lectures into a single PDF document, named whatever
# you want it to be (below named "all-lectures.pdf")
./CatenatePDFs.sh all-lectures.pdf
```

On the last step I get some warnings about Type 1 fonts, but I don't think that it is a problem.

ADDING R CODE COMPANIONS
------------------------

Eric has set this up so that each R code companion is an [R notebook](http://rmarkdown.rstudio.com/r_notebooks.html) that will live in this repository in the directory `R-notebooks`. If the notebook requires data or other input, that should be read out of \``R-notebooks/inputs`. (Using, for example, `readRDS("inputs/myfile.rds")`). Once the notebook is finished and has been reproducibly turned into an `nb.html` file, that `nb.html` file should be copied into `docs` from whence it will be served up on GitHub pages.

Eric has a crude way of indexing these things:

-   First, R-code companions should be named like `s02-20-random-walk-scattering-limiting.Rmd`. This says that it corresponds to session 2 (`s02`) around page 20.
-   Second, the title must be given in the notebook's YAML header
-   Finally, the YAML header must have a `description` line with a brief description of the R-code companion. This description must all be on a single line.

For example, the YAML header for `s02-20-random-walk-scattering-limiting.Rmd` looks something like this:

    ---
    title: "Random Walk with Scattering Boundaries, and Limiting Distributions"
    description: We devise a simple 5-state Markov chain, explore its properties, simulate from it and observe the consequences of the Weak Law of Large numbers for ergodic chains.
    output: 
      html_notebook:
        toc: true
    ---

When these conventions are followed, then knitting the file `docs/index.Rmd` produces an `index.html` that provides links to all the R-code companions.

So, the workflow is:

1.  Write a new R code companion, named appropriately, and with a description line.
2.  Once it is done, turn it into an nb.html file and move or copy that to `docs/`
3.  Open `docs/index.Rmd` and knit it.
4.  Commit all the new things and push em up to be stored and served off GitHub.

Then when students go to <http://eriqande.github.io/sisg_mcmc_course/> they get a list of R-code vignettes for the course.

LICENSE
-------

Copyright (C) 2014 Eric C. Anderson and Matthew Stephens with contributions from Mike Denham.

Permission is granted to copy, distribute and/or modify this document under the terms of the GNU Free Documentation License, Version 1.3 or any later version published by the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts. A copy of the license is included in file LICENSE.md.

Some of the style files are, where indicated, under the LaTeX Project Public License.
