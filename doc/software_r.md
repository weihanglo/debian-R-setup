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
test@server$ sudo vim /etc/apt/source.list
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
test@server$ sudo apt-key adv --keyserver keys.gnupg.net --recv-key 381BA480
```

- Finally, install R.
```bash
test@server$ sudo apt-get update
test@server$ sudo apt-get install r-base r-base-dev
```

- After the installation, execute this command to check the version of R in your server is up-to-date.
```bash
test@server$ R --version
```
