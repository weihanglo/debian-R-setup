# Backup your Server

As far as you are here, you may store lots of data in your server. Having duplicate copies of your most important files and keeping their safety is the urge thing to do.

There are a variety of methods of performing backups. Such as using [external hard drive][external-hdd], [third-party cloud storage][cloud], [storage area network][san] (SAN), and [network-attached storage][nas] (NAS). On software side, you have many awesome tools such as [`dd`][dd], [`dump`][dump], [`tar`][tar], as well as [`rsync`][rsync]. Every tool has its own advantages and disadvantages.
Here, we will introduce [`rsync`][rsync] and [NAS][nas] , two fo the most popular backup tools, for saving your life and time.

[external-hdd]: https://en.wikipedia.org/wiki/External_hard_drive
[cloud]: https://en.wikipedia.org/wiki/Cloud_storage
[nas]: https://en.wikipedia.org/wiki/Network-attached_storage
[san]: https://en.wikipedia.org/wiki/Storage_area_network
[dd]: https://en.wikipedia.org/wiki/Dd_(Unix)
[dump]: https://en.wikipedia.org/wiki/Dump_(program)
[tar]: https://en.wikipedia.org/wiki/Tar_(computing)
[rsync]: https://en.wikipedia.org/wiki/Rsync
