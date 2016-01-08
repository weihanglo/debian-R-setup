## Configure the "APT" Package manager
### Check The Network Connection

Although you've succeed the installation, you cannot do anything without configuring your source of your **package manager**.

Most Debian-based systems provied a powerful package manager called **Advanced Packaging Tool**, or **APT**. We can easily use **apt-get** command to install/remove open-source software in the Debian repository.


Before starting the configuraion, check the network connection in advance:
```bash
test@server$ ping www.gooogle.com
```

If you receive something like, it mean your connection is well:
```bash
PING www.google.com (74.125.203.105) 56(84) bytes of data.
64 bytes from th-in-f105.1e100.net (74.125.203.105): icmp_seq=1 ttl=46 time=15.6 ms
64 bytes from th-in-f105.1e100.net (74.125.203.105): icmp_seq=2 ttl=46 time=15.4 ms
64 bytes from th-in-f105.1e100.net (74.125.203.105): icmp_seq=3 ttl=46 time=15.6 ms
```

### Setup Archive Mirror Repository to Your Server

- Open **/etc/apt/source.list**
We will use **vi** to edit **source.list**. If you are not familiar to **vi**, use **nano** to substitube for **vi** in the command.
```bash
test@server$ sudo vi /etc/apt/source.list
```

- For an archieve mirror of Debian 8 (jessie) repository, simply add following lines into **sourece.list**.
```bash
deb http://<favourite-debian-mirror>/debian/ jessie main
deb-src http://<favourite-debian-mirror>/debian/ jessie main
```
_**NOTE**: You need to substitute_ `<favourite-cran-mirror>` _by one of the mirror URLs listed in the [mirror list](https://www.debian.org/mirror/list)._
_For example:_ `deb http://debian.csie.ntu.edu.tw/debian/ jessie main`

- Comment out the sources from CD/DVD
In the **source.list** file, there are some CD/DVD sources reserved for dealing some situation without network in the future. For now, they are useless and should be commented out:  
```bash
# deb cdrom:[Debian GNU/Linux 8.2.0 _Jessie_ - Official amd64 CD Binary-1 20150906-11:13]/ jessie contrib main
# deb cdrom:[Debian GNU/Linux 8.2.0 _Jessie_ - Official amd64 CD Binary-1 20150906-11:13]/ jessie contrib main
```

After all the commands above, you can install whatever your want in the Debian Repository.

### Let's learn some useful apt-get command:

- **apt-get update**: This command can resynchronize and update all packages from the sources. For security issue, ensure you update your server regulariry.
- **apt-get install/remove**: These command can simply install/remove packages you specified.
- **apt-get auroremove**: After you remove some pakcages, you may want to execute this command for **clean all the dependency**.

