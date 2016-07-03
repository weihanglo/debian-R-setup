## Rstudio Server
<img src="https://upload.wikimedia.org/wikipedia/en/f/f0/RStudio_logo.png" height="300px">

RStudio is a integrated development environment (IDE) for R. Also free, open 
source and multi-platform. It includes a console, graphic device, debugger, 
command history, and workspace management just like  a Matlab environment.

### Installation
To download and install RStudio Server. Execute the following commands. Note that **gdebi** should be installed first.
```bash
$ sudo apt-get update
$ sudo apt-get install gdebi-core
$ wget https://download2.rstudio.org/rstudio-server-0.99.491-amd64.deb
$ sudo gdebi rstudio-server-0.99.491-amd64.deb
```

To verify your installation, excute following command:
```bash
$ sudo rstudio-server verify-installation
```

### Simple Configuration
Simple commands for start/stop/restart server
```bash
$ sudo rstudio-server stop
$ sudo rstudio-server start
$ sudo rstudio-server restart
```

The default port for Rstudio server is **8787**. That means any can connect to the server through the URL **http://<server-ip/hostname>:8787**.  
If you wish to change to another port, you should add following configuration into **/etc/rstudio/rserver.conf** file. For example:
```bash
www-port=18787
```

Note that after any configuration, always restart server to apply your changes. 
```bash
$ sudo rstudio-server restart
```

Other tips:
- The users in Rstudio server are references to users of system.
- Each user needs to be created with a home directory.
- More tips on [Rstudio server support](https://support.rstudio.com/hc/en-us/sections/200150693-RStudio-Server).
