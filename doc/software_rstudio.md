## Rstudio Server
RStudio: a integrated development environment (IDE) for R. Also free, open source and multi-platform.
To start/stop/restart Rstudio server, use followings commands:

### Installation
To download and install RStudio Server. Execute the following commands. Note that **gdebi** should be installed first.
```bash
test@server$ sudo apt-get update
test@server$ sudo apt-get install gdebi-core
test@server$ wget https://download2.rstudio.org/rstudio-server-0.99.491-amd64.deb
test@server$ sudo gdebi rstudio-server-0.99.491-amd64.deb
```

To verify your installation, excute following command:
```bash
test@server$ sudo rstudio-server verify-installation
```

### Simple Configuration
Simple commands for start/stop/restart server
```bash
test@server$ sudo rstudio-server stop
test@server$ sudo rstudio-server start
test@server$ sudo rstudio-server restart
```

The default port for Rstudio server is **8787**. That means any can connect to the server through the URL **http://<server-ip/hostname>:8787**.  
If you wish to change to another port, you should add following configuration into **/etc/rstudio/rserver.conf** file. For example:
```bash
www-port=18787
```

Note that after any configuration, always restart server to apply your changes. 
```bash
test@server$ sudo rstudio-server restart
```

Other tips:
- The users in Rstudio server are references to users of system.
- Each user needs to be created with a home directory.
- More tips on [Rstudio server support](https://support.rstudio.com/hc/en-us/sections/200150693-RStudio-Server).
