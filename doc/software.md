# Softwares Installation and Other Configuration
Before starting any simulations or programming, you need to install some software:

- [Vim][vim]: Vi IMproved is a clone of vi editor for Unix.
- [R][r]: An open source, multi-platfrom language and environment for statistical computing and graphics.   
- [openssh][openssh]: Premier connectivity tool for remote login with the SSH protocol.
- [Rstudio Server][rstudio]: Productive user interface for R. Also free, open-source, and cross-paltform.
- [MariaDB][mariadb]: A popular database servers. Made by the original developers of MySQL.

[vim]: www.vim.org
[r]: https://www.r-project.org/
[rstudio]: https://www.rstudio.com/
[openssh]: http://www.openssh.com/
[mariadb]: https://mariadb.org/

While any package would have been tested thoroughly before included in a Debian 
stable release, the latest version of R and other packages won't be included in 
the repository. Hence, you need to add some additional repositories manually.

Now, we need an useful text editor. Let's download the poweful **Vim**.

## Vim
```bash
test@server$ sudo apt-get update
test@server$ sudo apt-get install vim
```

<img src="https://upload.wikimedia.org/wikipedia/commons/9/9f/Vimlogo.svg">
