# Dropbear SSH

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

Dropbear is a relatively small SSH server and client. It runs on a variety of unix platforms. Dropbear is open source software, distributed under a MIT-style license. Dropbear is particularly useful for "embedded"-type Linux (or other Unix) systems, such as wireless routers.

## Features

- A small memory footprint suitable for memory-constrained environments – Dropbear can compile to a 110kB statically linked binary with uClibc on x86 (only minimal options selected)
- Dropbear server implements X11 forwarding, and authentication-agent forwarding for OpenSSH clients
- Can run from inetd or standalone
- Compatible with OpenSSH ~/.ssh/authorized_keys public key authentication
- The server, client, keygen, and key converter can be compiled into a single binary (like busybox)
- Features can easily be disabled when compiling to save space
- Multi-hop mode uses SSH TCP forwarding to tunnel through multiple SSH hosts in a single command. dbclient user1@hop1,user2@hop2,destination

## Platforms

- Linux – standard distributions, uClibc, dietlibc, musl libc, uClinux from inetd
- Mac OS X (compile with PAM support)
- FreeBSD, NetBSD and OpenBSD
- Solaris – tested v8 x86 and v9 Sparc
- IRIX 6.5 (with /dev/urandom, or prngd should work)
- Tru64 5.1 (using prngd for entropy)
- AIX 4.3.3 (with gcc and Linux Affinity Toolkit), AIX 5.2 (with /dev/urandom).
- HPUX 11.00 (+prngd), TCP forwarding doesn't work
- Cygwin – tested 1.5.19 on Windows XP

## Tech

- [Dropbear SSH] - lightweight SSH server

### Installation

Install dropbear.

```
root@dev:~# sudo apt install dropbear
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwrap0 openssh-sftp-server ssh-import-id
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  dropbear-initramfs
Suggested packages:
  runit
The following NEW packages will be installed:
  dropbear dropbear-initramfs
0 upgraded, 2 newly installed, 0 to remove and 33 not upgraded.
Need to get 17.1 kB of archives.
After this operation, 97.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://se.archive.ubuntu.com/ubuntu focal/universe amd64 dropbear all 2019.78-2build1 [8084 B]
Get:2 http://se.archive.ubuntu.com/ubuntu focal/universe amd64 dropbear-initramfs all 2019.78-2build1 [8992 B]
Fetched 17.1 kB in 0s (95.5 kB/s)
Selecting previously unselected package dropbear.
(Reading database ... 71520 files and directories currently installed.)
Preparing to unpack .../dropbear_2019.78-2build1_all.deb ...
Unpacking dropbear (2019.78-2build1) ...
Selecting previously unselected package dropbear-initramfs.
Preparing to unpack .../dropbear-initramfs_2019.78-2build1_all.deb ...
Unpacking dropbear-initramfs (2019.78-2build1) ...
Setting up dropbear-initramfs (2019.78-2build1) ...
Generating Dropbear DSS host key.  Please wait.
Generating 1024 bit dss key, this may take a while...
1024 SHA256:zzKFcP2+rU0XiBCfbLX1/oR4uzeYsUHXTSXHDboG3Mg root@dev (DSA)
+---[DSA 1024]----+
|         .   .o+=|
|         ++oo.oo=|
|      . ..E=o. .+|
|       o .oo.+.+o|
|        S ..*.+.o|
|         + o + oo|
|        o o . O o|
|         o   O +.|
|            o.+..|
+----[SHA256]-----+
Generating Dropbear RSA host key.  Please wait.
Generating 2048 bit rsa key, this may take a while...
2048 SHA256:l1/gpfNj7C0MX7L9RlPokDQ9813ZlxlVQcxuzF+JVJQ root@dev (RSA)
+---[RSA 2048]----+
|             .**&|
|            o.+E+|
|           .oo*==|
|           oo=.*=|
|        S o +oo +|
|         . ..=o.+|
|            .+=*.|
|             o=oo|
|              .o+|
+----[SHA256]-----+
Generating Dropbear ECDSA host key.  Please wait.
Generating 256 bit ecdsa key, this may take a while...
256 SHA256:Q9faes8tSY14ykgRzeFGkAcTp4+838Ggb/9WGUeahTg root@dev (ECDSA)
+---[ECDSA 256]---+
|          =B+o . |
|          oBE . o|
|        . oo+. = |
|       . o.*  o..|
|        S +.+. o+|
|         ..+.o+.o|
|         .+o.+o..|
|          .+++oo.|
|           .o.=+o|
+----[SHA256]-----+
update-initramfs: deferring update (trigger activated)
Dropbear has been added to the initramfs. Don't forget to check
your "ip=" kernel bootparameter to match your desired initramfs
ip configuration.

Setting up dropbear (2019.78-2build1) ...
# the TCP port that Dropbear listens on
DROPBEAR_PORT=22

# any additional arguments for Dropbear
DROPBEAR_EXTRA_ARGS=

# specify an optional banner file containing a message to be
# sent to clients before they connect, such as "/etc/issue.net"
DROPBEAR_BANNER=""

# RSA hostkey file (default: /etc/dropbear/dropbear_rsa_host_key)
#DROPBEAR_RSAKEY="/etc/dropbear/dropbear_rsa_host_key"

# DSS hostkey file (default: /etc/dropbear/dropbear_dss_host_key)
#DROPBEAR_DSSKEY="/etc/dropbear/dropbear_dss_host_key"

# ECDSA hostkey file (default: /etc/dropbear/dropbear_ecdsa_host_key)
#DROPBEAR_ECDSAKEY="/etc/dropbear/dropbear_ecdsa_host_key"

# Receive window size - this is a tradeoff between memory and
# network performance
DROPBEAR_RECEIVE_WINDOW=65536
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
"/etc/default/dropbear" 22L, 753C                                                                                                                             1,1           All
# the TCP port that Dropbear listens on
Generating Dropbear DSS host key.  Please wait.
Generating 1024 bit dss key, this may take a while...
1024 SHA256:9z1L3W2zoz9Yn5h69OnfpAAM/zX9Bov3nXlrczY46cA root@dev (DSA)
+---[DSA 1024]----+
|                 |
|                 |
|        .        |
|         +     . |
|        S =   + .|
|         ..+ = *+|
|           E* #.%|
|            .% ^%|
|           .+oOO#|
+----[SHA256]-----+
Generating Dropbear RSA host key.  Please wait.
Generating 2048 bit rsa key, this may take a while...
2048 SHA256:CZmxg8mZgneZ2Xuc/BQGbotxcOM7Qg06xdjJpFleu4Y root@dev (RSA)
+---[RSA 2048]----+
|     *B.=        |
| . ..^=& +       |
|. o / @ B o      |
| . o o % B .     |
|      E S .      |
|       + +       |
|          .      |
|                 |
|                 |
+----[SHA256]-----+
Generating Dropbear ECDSA host key.  Please wait.
Generating 256 bit ecdsa key, this may take a while...
256 SHA256:k2vMPxgkVUy+wf7ksaakMnq/Q2deBGZZmfVvzqXtnQ4 root@dev (ECDSA)
+---[ECDSA 256]---+
|         +oo.+.  |
|        .o* o  . |
|       . o+.    .|
|      . .o o.   .|
|       oS o.o   +|
|       oooo+.o *.|
|       .=*..=E. +|
|      +.o+oo  ..o|
|    .o ++oo.  .oo|
+----[SHA256]-----+
Processing triggers for systemd (245.4-4ubuntu3.11) ...
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-89-generic
dropbear: WARNING: Invalid authorized_keys file, remote unlocking of cryptroot via SSH won't work!
```
### Configuration

Enable firewall and open port 30042 for incoming connections.

```sh
root@dev:~# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
```

```sh
root@dev:~# ufw allow 30042/tcp
Rule added
Rule added (v6)
```

Change the target port to 30042.

```sh
root@dev:~# nano /etc/default/dropbear
```

Confirm that's been changed.

```sh
root@dev:~# cat /etc/default/dropbear | grep DROPBEAR_PORT
DROPBEAR_PORT=30042
```

Restart dropbear first so changes take effect
```
root@dev:/# systemctl restart dropbear
```

## Copy SSH keys to server

```
❯ ssh-copy-id john@192.168.0.15
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/Users/john/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
john@192.168.0.15's password:

Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'john@192.168.0.15'"
and check to make sure that only the key(s) you wanted were added.
```



### Connect to OpenSSH without password

```
❯ ssh john@192.168.0.15
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-91-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Wed 01 Dec 2021 11:08:39 AM UTC

  System load:             0.0
  Usage of /:              46.5% of 8.79GB
  Memory usage:            22%
  Swap usage:              0%
  Processes:               110
  Users logged in:         0
  IPv4 address for enp0s3: 192.168.0.15
  IPv6 address for enp0s3: fdaa:bbcc:ddee:0:a00:27ff:fefd:c60d


40 updates can be applied immediately.
To see these additional updates run: apt list --upgradable


Last login: Wed Dec  1 11:08:08 2021 from 192.168.0.4
```

### Configure SSH Keys for Dropbear
```
root@dev:~# ln  ~/.ssh/authorized_keys  /etc/dropbear/
root@dev:~# chmod 600 /etc/dropbear/authorized_keys
root@dev:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
30042/tcp                  ALLOW IN    Anywhere
22/tcp                     ALLOW IN    Anywhere
30042/tcp (v6)             ALLOW IN    Anywhere (v6)
22/tcp (v6)                ALLOW IN    Anywhere (v6)
```


### Now you can also connect to Dropbear without password
```
❯ ssh -p 30042 john@192.168.0.15
john@dev:~$
```
   [Dropbear SSH]: https://matt.ucc.asn.au/dropbear/dropbear.html
