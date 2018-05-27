# FUSE

FUSE, short for Filesystems in USEr space, offers yet another potentially powerful way to emulate GPIO access in Linux.

The power of FUSE lies in that it enables the creation of custom filesystems without creating dedicated kernel modules for each filesystem [#]. Moreover, all of this is available to the normal user of the system, no super user, or "root", access is required.

![Regular filesystem access \label{6_0_1}](source/figures/6_0_1.png)

FUSE consists of two parts: a kernel driver and a User space FUSE client which talks to the kernel driver. The way it works is that a client filesystem, running in User space, asks the FUSE kernel module to mount a new filesystem. Any file operations directed at that mount point, such as trying to list the content of a directly, is then forwarded to the client filesystem. The client filesystem can then handle these requests in any way it wants.

![Accessing a FUSE filesystem \label{6_0_2}](source/figures/6_0_2.png)

FUSE has been a part of mainstream Linux since Linux Kernel version 2.6.14, released in 2005 [@linux-git-log-added-fuse].

## FUSE Security
A mounted FUSE filesystem is normally only available to the user that mounted the filesystem. This can be overridden to extend to all users with a configuration option.

## Example: Encrypted filesystem
How FUSE works, and how it could be useful, could easily be illustrated with EncFS.

EncFS [#] is a command-line tool which takes two arguments, a `RootDirectory` and a `MountDirectory`. When run, it will create a new mount point at the `MountDirectory`. Any writes to this directory, such as creating a new file, will be intercepted, encrypted, and store in its encrypted form in `RootDirectory`. Whenever a file is read, it will first be decrypted and then returned. For the end-user, this will be completely transparent.

![EncFS encryption flow \label{6_2_0_1}](source/figures/6_2_0_1.png)

![EncFS decryption flow \label{6_2_0_2}](source/figures/6_2_0_2.png)

EncFS runs completely in User space where it uses the FUSE kernel module to intercept all calls to files inside the `MountDirectory`.