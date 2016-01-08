# Softwares Installation and Other Configuration
## Useful Softwares and Services
Before starting any simulations or programming, you need to install the following software:

- [Vim][vim]: Powerful text editor.
- [R][r]: An open source, multi-platfrom language and environment for statistical computing and graphics.   
- [openssh][openssh]: Premier connectivity tool for remote login with the SSH protocol.
- [Rstudio Server][rstudio]: Productive user interface for R. Also free, open-source, and cross-paltform.
- [MariaDB][mariadb]: A popular database servers. Made by the original developers of MySQL.

While any package would have been tested thoroughly before included in a Debian stable release, the latest version of R and other packages won't be included in the repository. Hence, you need to add some additional repositories manually.

The following steps are all done in command line (or terminal emulator).

[vim]: www.vim.org
[r]: https://www.r-project.org/
[rstudio]: https://www.rstudio.com/
[openssh]: http://www.openssh.com/
[mariadb]: https://mariadb.org/

## Vim
```bash
test@server$ sudo apt-get update
test@server$ sudo apt-get install vim
```

## R
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

