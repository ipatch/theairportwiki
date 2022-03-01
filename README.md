<div align="center">

<img src="https://img.shields.io/static/v1?label=libera.chat&message=%23theairportwiki&color=blue"></img>

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

### Usage / `smbclient`

went to down a bit of a rabbit hole today messing around with the `smbclient` cmd on my arch linux box, trying to connect to my time capsule using `smbclient`. i can obviously connect to it and mount with the above mentioned commands, but wanted to connect to it using `smbclient` just for the understanding of it.

```shell
echo "first if ip address or server name is uknown use nmap to find the ip address"
nmap -sT "10.0.1.*"; echo "obviously searching on a LAN, and knowing that the ip range is in the "10.0.1.x"
```

```
# output
Nmap scan report for 10.0.1.1

139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
```

```
nmblookup -A 10.0.1.1
Looking up status of 10.0.1.1
        SNOWBRICK       <00> -         B <ACTIVE> <PERMANENT>
        WORKGROUP       <00> - <GROUP> B <ACTIVE> <PERMANENT>
        SNOWBRICK       <20> -         B <ACTIVE> <PERMANENT>

        MAC Address = 44444444444444444
```

then try and connect to the smb server, (unfortunately my apple time capsule only supports samba server version 1)

```
smbclient -L 10.0.1.1
```

```
# output
protocol negotiation failed: NT_STATUS_INVALID_NETWORK_RESPONSE
```

```
smbclient -L \\SNOWBRICK
```

⚠️ since the apple time capsule is running netbsd v4.0 and such an old version of the samba server certain options will need to be set in order to interact with the server

```
smbclient //SNOWBRICK/Data --option='client min protocol=nt1' --option='client use spnego=no' --password $TCPASSWORD
```

i got the same results using all the servernames

```
smbclient //snowbrick
smbclient //SNOWBRICK
smbclient //10.0.1.1
```

to avoid having to the two options `--option='client min protocol=nt1' --option='client use spnego=no` everytime using the `smbclient` cmd add the below line to `/etc/samba/smb.conf`

```
# smb.conf
[global]
client use spnego=no
client use min protocol=nt1
```


🔥🔥🔥🔥

```
smbclient //snowbrick/data --password $TCPASSWORD
```
