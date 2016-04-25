## Rsync

[**Rsync**][rsync], standing for **Remote SYNChorize**, is an open source tool which provide fast incremental file transfer. As same as `scp` command, `rsync` can simply transfer data via ssh/rsh. More over, `rsync` itself can also be a daemon if needing for lower CPU overhead and faster transfer rate.

[rsync]: https://rsync.samba.org/

### Two different way for use rsync to contact a remote system

#### 1. Using a remote-shell program as the transport (ssh/rsh):

Remote-shell transport format would be familiar to you. A single colon **(:)**
separate a host specification and source/destination path.

To sync files from remote to local is just like cp/scp:

```bash
test@server$ rsync user@hostname:path/to/file /path/to/syncfile
```

Or backup to remote

```bash
test@server$ rsync /path/to/file user@hostname:path/to/syncfile
```

If you use non-default port for your remote-shell program, or want to add some 
different feature while transfer via ssh/rsh, just add specified remote-shell 
command after `-e` option:

```bash
test@server$ rsync -e 'ssh -p 10022' user@hostname:path/to/syncfile
```

#### 2. Contacting an rsync daemon directly via TCP

A rsync daemon is mostly used when your want to constantly maintain a synchronization. It can save some CPU usage and speedup transfer rate a bit.

To use rsync daemon for sync, a double colon **(::)** is required to separate the host specification and the module, or using `rsync://` schema. Using double colon almost the same as single colon. The only difference is the **module** parameter. We will cover it later.

The default rsync daemon TCP port typically using **873**.

```bash
test@server$ rsync user@hostname::module /path/to/syncfile
```

However, rsync daemon would not encrypt data while transfering by default, you should manually encrypt by `ssh` command as your needs. (Encryption may lower some speed, but is necessary when connecting to internet.)

```bash
test@server$ rsync -e 'ssh' user@hostname::path/to/file /path/to/syncfile
```

The `rsync` schema is another way to do the same thing:
```bash
# Example for rsync:// schema
# rsync [OPTION]... rsync://[USER@]HOST[:PORT]/MODULE[/SRC] [DEST]
rsync rsync://test@server/module /path/to/your/copyfile
```

*__ATTENTAION!!__* : 
rsync has a trick that if the source path without an trailling slash, it would create a directory with the same name inside the destination directory. Otherwise, it would only sync files inside source directory.
```bash
# This will sync files with the directory.
rsync /directory-no-slash /path/to/store/a/new/directory

# This will sync files under the directory.
rsync /directory-no-slash/ /path/to/store/some/new/files
```

### Useful rsync options
Here are some common options for rsync

- `-a` : archive mode, the same as using `-rlptgoD`.
  + `-r` : rescursive
  + `-l` : copies symlinks as symlinks
  + `-p` : preserves permissions 
  + `-t` : preserves modification times
  + `-g` : preserves group
  + `-o` : preserves owner
  + `-D` : preserves device files
- `-A` : preserves ACLs (A more specific access rights table. See [wiki][acl].)
- `-H` : preserves hard links
- `-S` : handle sparse files efficiently
- `-X` : preserves extended attributes
- `-v` : increase verbosity (can add up to tree `-vvv` for the most verbosity)
- `-x` : don't cross file-system boundaries (A filesystem boundary is a mount point. [See more][fs-boundary]!)
- `-z` : compress data during the transfer
- `--delete` : differential clean-up during sync, like a mirror backup
- `--numeric-ids` : do not map uid/gid values by user/group name
- `--progress` : show the transfer progress during
- `--password-file=**FILE**` : read rsync-daemon-access password from this **FILE**

Following rsync combined with options is the most usefule combination I've used.

```
rsync -aHAXzxv --numeric-ids --delete --progress -e "ssh -T -o Compression=no -x" [USER@]HOST:[SOURCE] [DEST]
```

### Rsync daemon
As mentioned above, using rsync daemon have a bit advantage when sync constantly. To setup a rsync daemon is as simple as setting up a ssh server. For convenience, We will explian how to setup a daemon with a Network-attached Storage in the next chapter.

[acl]: https://en.wikipedia.org/wiki/Access_control_list
[fs-boundary]: http://unix.stackexchange.com/questions/107113/meaning-of-crossing-filesystem-boundaries-one-file-system-etc
