<div align="center">
<a href="http://webchat.freenode.net?channels=%23theairportwiki" target="_blank"><img src="https://img.shields.io/badge/irc.freenode.net-%23theairportwiki-blue.svg?style=flat"  height="20"></a>
</div>
<br />
<div align="center">
<h1><a href="http://theairportwiki.com">TheAirPortWiki</a></h1>
</div>
<br />

<div align="center">

> _You cannot help men permanently by doing for them what they will not do for themselves._<br />

</div>

<div align="right">

***- Abraham Lincoln***

</div>

<div align="center">

### The [soon to be wiki](https://github.com/ipatch/theairportwiki/wiki) for TheAirPortWiki

</div>

##

<div align="center">
<img src="https://github.com/ipatch/theairportwiki/blob/ipatch/dev/media/airport-awesome-blue.JPG" alt="blue led on airport extreme" width="400">
</div>

##

## GitHub wiki development

When uploading a image within the `.wiki/lib` directory append the below URL in front of the image name within the `lib` dir to link against the image within this repo or wherever  🌈 else.

```shell
https://raw.githubusercontent.com/wiki/ipatch/theairportwiki/lib/
```

## Usage

<a name="usage"></a>

When working with Apple Time Capsule disks for a modern GNU+Linux distro, ie. Arch the below command will help mount the disk using CIFS

```shell
echo "mount the tc disk"
sudo -E mount.cifs //[tc.IP]/[PATH] [/local/path] -o "pass=[TC.DISK.PASSWORD],sec=ntlm,vers=1.0,file_mode=0777,dir_mode=0777,username=[$USER],uid=1000,gid=985"
echo "copy cmd"
rsync -a --no-o --no-g -h --info=progress2 -P /local/disk.qcow2 /local/path/
```

Note, I'm averaging about 10MB/s using rsynce to copy a large ~ 60GB qcow file across a network using a macbook with a gigabit to thunderbolt adapter, and writing the file to a SSD disk i installed in the time capsule.

Not exactly sure where the bottleneck on the network is arising, but my hunch makes me think write performance of the disk or server software running on the TC. (will test on a separate server in the future).
