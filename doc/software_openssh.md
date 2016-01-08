## OpenSSH
### Installation

Normally the client and server are installed by default. If not it suffices to run:
```bash
test@server$ sudo apt-get update
test@server$ sudo apt-get install openssh-client openssh-server
```

### Simple Configuration

The main configuration files are in the directory **/etc/ssh**:

**ssh_config** : client configuration file
**sshd_config** : server configuration file 

We will only cover the server configuration in this manual.

- Open **/ect/ssh/sshd_config** for editing.
```bash
test@server$ sudo vim /etc/ssh/sshd_config
```

- For security, change the listening port instead of default TCP port 22 as such:
```bash
Port 10022
```

- Ensure that **PermitRootLogin** is set to **no** in sshd_config (we use sudo-user only):
```bash
PermitRootLogin no
```

- Start your SSH service.
```bash
test@server$ sudo /etc/init.d/ssh start
```


_**NOTE:** After any configuration, always restart server to apply your changes._
```bash
test@server$ sudo /etc/init.d/ssh restart
```

