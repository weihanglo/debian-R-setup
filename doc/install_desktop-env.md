## Optional: Install Graphical User Desktop Environment
If you are not comfortable with command line interface, you can download your favorite desktop environment such as Gnome or KDE from the Debian repository. Following are some commands to install them.

### Gnome Desktop Environment (GDM)
<img src="https://www.gnome.org//wp-content/uploads/2013/06/gnome-logos.png">

The [GNOME][gnome] Desktop Enviroment is an fantastic-looking, modern, and useful desktop environment. [GNOME][gnome] is both free and one of the most widely used desktop environments on the GNU/Linux operating system.  

To install it, first make sure that tasksel and aptitude are installed:
```bash
test@server$ sudo apt-get install aptitude tasksel
```

Then, install the GNOME task:
```bash
test@server$ sudo tasksel install gnome-desktop --new-install
```

Screenshot:  
<img src="https://www.gnome.org/wp-content/uploads/2010/09/activities-overview-940x529.png">

### LXDE (Lightweight X11 Desktop Environment)
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/LXDE-logo.svg/551px-LXDE-logo.svg.png" height="300px">
[LXDE][lxde] is a free desktop environment with comparatively low resource requirements. It is recommanded if you only need basic operation with graphical interface.   
To install a complete Debian [LXDE][lxde] desktop environment, execute commands below:
```bash
test@server$ sudo apt-get update
test@server$ sudo apt-get install task-lxde-desktop
```

Screenshot:  
<img src="http://lxde.org/sites/default/files/images/desktop_full.preview/index.png">

### Start X-session
After the installation, you can simply enter the desktop environment by execute the command:
```bash
test@server$ startx
```

_**NOTE:** Click [here][dm-guide] for more desktop environment installation guide._

[gnome]: https://www.gnome.org/
[lxde]: http://lxde.org/
[dm-guide]: https://wiki.debian.org/DesktopEnvironment
