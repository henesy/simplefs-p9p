# simplefs (plan9port)

**Partially broken**

Demonstrative fs that's a reduction of the framework shown in semfs by Nemo.

Simplefs accepts writes to the ctl file, logs the message, then prints out its history in the log file.

Currently operations on directories don't work, but you can use the 9p(1) tool from plan9port or [my 9p(1)](https://github.com/henesy/9p) to interact with the file system.

9pfs will fail.

## Build

	mk

## Install

	mk install

## Usage

An example session:

	$ 9p -a 'unix!'`namespace`/sfs ls /ctl
	2020/09/23 00:35:13 Error, dir decode failed for ls: unexpected EOF
	$ 9p -a 'unix!'`namespace`/sfs read /ctl
	ctl file is unreadable.
	$ 9p -a 'unix!'`namespace`/sfs read /log
	asdf
	asdf
	asdf
	asdf
	$ 9p -a 'unix!'`namespace`/sfs ls /
	2020/09/23 00:36:27 Error, walk for stat failed: 9p: no such directory.
	$

## References

- [9p(5)](http://man.postnix.us/9front/5/intro)
- [semfs](https://bitbucket.org/henesy/9intro/src/default/ch13/semfs/)
- [ctlfs](http://contrib.9front.org/mischief/sys/src/cmd/proc/src/core/ctlfs.c)
- [lib9p/ramfs](http://mirror.postnix.us/plan9front/sys/src/lib9p/ramfs.c)
