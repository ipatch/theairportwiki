<div align="center">

<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="164" height="20" role="img" aria-label="libera.chat: #theairportwiki"><title>libera.chat: #theairportwiki</title><linearGradient id="s" x2="0" y2="100%"><stop offset="0" stop-color="#bbb" stop-opacity=".1"/><stop offset="1" stop-opacity=".1"/></linearGradient><clipPath id="r"><rect width="164" height="20" rx="3" fill="#fff"/></clipPath><g clip-path="url(#r)"><rect width="69" height="20" fill="#555"/><rect x="69" width="95" height="20" fill="#007ec6"/><rect width="164" height="20" fill="url(#s)"/></g><g fill="#fff" text-anchor="middle" font-family="Verdana,Geneva,DejaVu Sans,sans-serif" text-rendering="geometricPrecision" font-size="110"><text aria-hidden="true" x="355" y="150" fill="#010101" fill-opacity=".3" transform="scale(.1)" textLength="590">libera.chat</text><text x="355" y="140" transform="scale(.1)" fill="#fff" textLength="590">libera.chat</text><text aria-hidden="true" x="1155" y="150" fill="#010101" fll-opacity=".3" transform="scale(.1)" textLength="850">#theairportwiki</text><text x="1155" y="140" transform="scale(.1)" fill="#fff" textLength="850">#theairportwiki</text></g>
</svg>

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
