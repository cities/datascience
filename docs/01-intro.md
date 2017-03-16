# Introduction

## Readings

1.	Davenport, T.H., Patil, D.J., 2012. Data Scientist: The Sexiest Job of the 21st Century. Harvard Business Review. URL https://hbr.org/2012/10/data-scientist-the-sexiest-job-of-the-21st-century (accessed 2/10/2017).
1. [R4DS] Chapter 1, 6, 8
1.	Wilson, G., Aruliah, D.A., Brown, C.T., Hong, N.P.C., Davis, M., Guy, R.T., Haddock, S.H.D., Huff, K., Mitchell, I.M., Plumbley, M., Waugh, B., White, E.P., Wilson, P., 2012. Best Practices for Scientific Computing. arXiv:1210.0530. URL https://arxiv.org/abs/1210.0530 (accessed 3/7/17).

## Introduction

### Best practices for data science (Wilson et al, 2012)

1. Write programs for people, not computers.
    1. a program should not require its readers to hold more than a handful of facts in memory at once
    1. make names consistent, distinctive, and meaningful 
    1. make code style and formatting consistent
1. Let the computer do the work
    1. make the computer repeat tasks
    1. save recent commands in a file for re-use
    1. use a build tool to automate workflows
1. Make incremental changes
    1. work in small steps with frequent feedback and course correction
    1. use a version control system
    1. put everything that has been created manually in version control 
1. Don’t repeat yourself (or others)
    1. every piece of data must have a sin- gle authoritative representation in the system 
    1. modular- ize code rather than copying and pasting
    1. re-use code instead of rewriting it
1. Plan for mistakes
    1. add assertions to programs to check their operation 
    1. use an off-the-shelf unit testing library
    1. turn bugs into test cases
    1. use a symbolic debugger
1. Optimize software only after it works correctly
    1. use a profiler to identify bottlenecks
    1. write code in the highest-level language possible
1. Document design and purpose, not mechan- ics.
    1. document interfaces and reasons, not imple- mentations
    1. refactor code in preference to explaining how it works
    1. embed the documentation for a piece of software in that software
1. Collaborate
    1. use pre-merge code reviews
    1. use pair programming when bring- ing someone new up to speed and when tackling particularly tricky problems
    1. use an issue tracking tool

### The tidyverse work flow

Data Science is a discipline that combines computing with statistics. A data analysis problem is solved in a series of data-centric steps: data acquisition and representation (Import), data cleaning (Tidy), and an iterative sequence of data transformation (Transform), data modelling (Model) and data visualization (Visualize). The end result of the process is to communicate insights obtained from the data (Communicate). This class will take you through all the steps in the process and will teach you how to approach such problems in a systematic manner. You will learn how to design data analysis pipelines as well as how to implement data analysis pipelines in R. The class will also emphasize how elegant code leads to reproducible science.

1. Import your data into R
2. Tidy it
3. Understand your data by iteratively
  - visualizing
  - tranforming and
  - modeling your data
4. Communicate your results to an audience

Program and automate your analysis for easy reuse the whole way through, since you do each of these things on a computer. For this course, we focus on the tidyverse packages namely:

* ggplot2, for data visualisation.
* dplyr, for data manipulation.
* tidyr, for data tidying.
* readr, for data import.
* purrr, for functional programming.
* tibble, for tibbles, a modern re-imagining of data frames.

For more R packages you can use for the tidyverse workflow see [list here](https://github.com/rstudio/RStartHere)

![Figure tidyverse workfow](http://r4ds.had.co.nz/diagrams/data-science.png) 

## R and RStudio

### Installation

* Install [R, a free software environment for statistical computing and graphics](http://www.r-project.org) from [CRAN](https://cran.r-project.org), the Comprehensive R Archive Network. Download a precompiled binary distribution for your operating system at https://cran.r-project.org/ and follow the prompt to install.

* Install RStudio's IDE (stands for _integrated development environment_), a powerful user interface for R. Get the Open Source Edition of RStudio Desktop from https://www.rstudio.com/products/rstudio/download/. 

Even though it is possible to directly work with the bare R, RStudio provides a much friendlier interface to R and we thus primarily use RStudio as our main interface to R. Since RStudio depends on R, you can not install RStudio without installing R first.

If you have a pre-existing installation of R and/or RStudio, we __highly recommend__ that you reinstall both and get as current as possible. It can be considerably harder to run old software than new.

  * If you upgrade R, you will need to update any packages you have installed. The command below should get you started, though you may need to specify more arguments if, e.g., you have been using a non-default library for your packages.

``` r
update.packages(ask = FALSE, checkBuilt = TRUE)
```

### Testing testing

* Do whatever is appropriate for your OS to launch RStudio. You should get a window similar to this screenshot 

![RStudio Screenshot](http://www.rstudio.com/wp-content/uploads/2014/04/rstudio-workbench.png).

* Put your cursor in the pane labelled Console, which is where you interact with the live R process. Create a simple object with code like (followed by enter or return):


```r
x <- 2 * 4
```

Then inspect the `x` object by typing `x` followed by enter or return. You should see the value 8 print to screen. If yes, you've succeeded in installing R and RStudio.


```r
x
```

```
## [1] 8
```

### Add-on packages

R is an extensible system and many people share useful code they have developed as a _package_ via CRAN. To install a package from CRAN, for example the [`dplyr`](https://cran.rstudio.com/web/packages/dplyr/vignettes/introduction.html)  package for data manipulation, here is one way to do it in the R console (there are others, for example, you can use the _Packages_ tab of RStudio to install/update R packages).

```r
install.packages("dplyr", dependencies = TRUE)
```

By including `dependencies = TRUE`, we are being explicit and extra-careful to install any additional packages the target package, `dplyr` in the example above, needs to have around.

You could use the above method to install the meta package `tidyverse` we will cover in this course:

```r
install.packages("tidyverse", dependencies = TRUE)
```

Nowadays a lot of R package developers share their R package via github (Hadley Wickham being of one of them through https://github.com/hadley/). You can install R packages from GitHub with:

```r
install.packages("devtools")
devtools::install_github("richfitz/remake") 
#remake is a workflow automation tools that is not (yet) available on CRAN
```

### R and RStudio tutorial

The RStudio interface is divided into panes for Editing, Console, Environment/History and Misc. You will learn to work with it throughout this course. If you feel you need a tutorial to get familar with RStudio, you can find one at [Introduction to R and RStudio](https://www.sitepoint.com/introduction-r-rstudio/).

### Project orgnization in RStudio

R experts keep all the files associated with a project together — input data, R scripts, analytical results, figures. This is such a wise and common practice that RStudio has built-in support for this via projects. For example, a project can be a R package under development, or code, data and documents for a research project, or a book project (for example, Hadley use a RStudio project for the R for Data Science book at https://github.com/hadley/r4ds). 

A RStudio project must contain a file with extension Rproj and can contain any files within the directory where the project file lives or its subdirectories. Typical types of files in a RStudio project include:
  - R Script
  - R Markdown, R notebook
  - R Presentation
  - Shiny Web App
  - Text file, C++, html, ...

Hadley recommends the following for RStudio projects workflow:

- Create an RStudio project for each data analyis project.
- Keep data files there and load them into R with data import.
- Keep scripts there; edit them, run them in bits or as a whole.
- Save your outputs (plots and cleaned data) there.
- Only ever use relative paths (relative to the root path of the project), not absolute paths.

Everything you need is in one place, and cleanly separated from all the other projects that you are working on.

I recommend organizing files in subdirectories by types, typically with at least these items:
  - project_name.Rproj, RStudio project file
  - README.md, a description file of the project
  - code, for R scripts
  - data, for data files
  - docs, for document/report files, such as R Markdown files

### Set up github and clone datascience course repository



## Learning more

The above will get your basic setup ready but here are some links if you are interested in reading a bit further.

  * RStudio Cheat Sheet
    - <https://www.rstudio.com/wp-content/uploads/2016/01/rstudio-IDE-cheatsheet.pdf>
  * RStudio's leads for getting help with R
    - <https://support.rstudio.com/hc/en-us/articles/200717153-Getting-Help-with-R>
  * R FAQ:
    - <http://cran.r-project.org/doc/FAQ/R-FAQ.html>
  * R Installation and Administration
    - <http://cran.r-project.org/doc/manuals/R-admin.html>
  * More about add-on packages in the R Installation and Administration Manual
     - <https://cran.r-project.org/doc/manuals/R-admin.html#Add_002don-packages>