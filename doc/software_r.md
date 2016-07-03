## R
<img src="https://www.r-project.org/Rlogo.png" alt="R" height=100>

The R language is widely used among statisticians and data miners for developing 
statistical software and data analysis. Nowadays, R and Python are both part of
a typical data science workflow.  

See [Why you should learn R first for data science][why-r].  
[why-r]: http://www.r-bloggers.com/why-you-should-learn-r-first-for-data-science/

For downloading latest version of R, adding additional repositories to debian repository list is required.

- For a backport of latest R to Debian 8 (jessie), simply open **/etc/apt/sourece.list**.
```bash
$ sudo vim /etc/apt/source.list
```

- Then add following lines into **/etc/apt/sourece.list**.
```bash
deb http://<favourite-cran-mirror>/bin/linux/debian jessie-cran3/
deb-src http://<favourite-cran-mirror>/bin/linux/debian jessie-cran3/
```
_**NOTE**: You need to substitute_ `<favourite-cran-mirror>` _by one of the mirror URLs listed in the [mirror list](http://cran.r-project.org/mirrors.html)._   
_For example:_ `deb http://cran.csie.ntu.edu.tw/bin/linux/debian jessie-cran3/`.

- Fetch and import Debian backports archives on CRAN (CRAN Debian archive) with key ID 381BA480.
```bash
$ sudo apt-key adv --keyserver keys.gnupg.net --recv-key 381BA480
```

- Finally, install R.
```bash
$ sudo apt-get update
$ sudo apt-get install r-base r-base-dev
```

- After the installation, execute this command to check the version of R in your server is up-to-date.
```bash
$ R --version
```

### Useful R packages

One feature of R is its capabilities to extend through third-party packages. 
Currently, the [CRAN][cran] package repository features 7749 available packages 
(2015-01-09). There are also many [Task Views][cran] for R users to browse
packages for differenct area of interest.  

[cran]: https://cran.r-project.org/
[task-views]: https://cran.r-project.org/web/views/

We will introduce some useful packages here.

[plyr][plyr]/[dplyr][dplyr]: Fast, consistent tools for data manipulating, both 
in or out of memory.  
[data.table][data.table]: An extension of data.frame for large data.  
[ggplot2][ggplot2]: A plotting system for R, based on the grammar of graphics.
[spatstat][spatstat]: Spatial statistics focusing on spatial point patterns.  
[installr][installr]: Make updating R (on windows) as easy as running a function.  
[rmarkdown][rmarkdown]: Enable easy creation of dynamic documents, 
presentations, and reports from R.  
[DBI][DBI]: A database interface for communication between R and relational 
database management systems.  


[plyr]: http://plyr.had.co.nz/
[dplyr]: https://cran.rstudio.com/web/packages/dplyr/vignettes/introduction.html
[data.table]: https://github.com/Rdatatable/data.table/wiki
[ggplot2]: http://ggplot2.org/
[spatstat]: http://spatstat.github.io/
[installr]: https://github.com/talgalili/installr
[rmarkdown]: http://rmarkdown.rstudio.com/
[DBI]: https://cran.r-project.org/web/packages/DBI/README.html
