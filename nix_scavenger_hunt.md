# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*
/home/luke

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*
Desktop           Pictures
Documents         Public
Downloads         Templates
examples.desktop  Videos
Music             wats1030-intro-to-unix-master



* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*
Can see permissions, owners, file size, and date modified

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://linux.die.net/man/)Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*
-a: do not ignore entries starting with .
-h: Human-readable
-l: Long-listing format


* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*
bin    initrd.img      mnt   snap  vmlinuz
boot   initrd.img.old  opt   srv   vmlinuz.old
cdrom  lib             proc  sys
dev    lib64           root  tmp
etc    lost+found      run   usr
home   media           sbin  var



* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*
/


* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*
/home/luke

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*
I used -X to sort by extension type. found 3 .demo files

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*
/home/luke/wats1030-intro-to-unix-master

* Press the up arrow on your keyboard. *What just happened?*
Command pwd was entered

* Press the up arrow a few more times. *What do you see?*
Sorts through my most recent commands

* Run the `history` command. *What do you see?*
I can see all my most recent commands. Listing about 45 of them.

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*
luke

* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*
luke     tty7         2016-07-03 18:09 (:0)
Just me. Fresh virtual machine. Is tty7 my user type?

* How long has your system been running? Use `uptime` to see, and *paste the result here:*
 18:25:57 up 16 min,  1 user,  load average: 0.45, 0.37, 0.40


* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*
These are the current processes that are running. Or a snapshot of what was happening when I entered the command. Scrolling to the top shows User, PID, CPU%, mem%, vsz, rss, tty, stat, start, time, command.


* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*
This is a live view of what ps aux was from what I can tell.

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*
2


* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*
01-15-2015

* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*
/home/luke/wats1030-intro-to-unix-master/challenge_files/tmp/modi_laboriosam.txt


* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*
2

* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*
serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt consectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.



### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*
Appears to be a file list from challenge_files


* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*
I have to hit the space bar to scroll down when I want to see more files listed.


* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*
ps aux | grep luke
avahi      601  0.0  0.1  44920  2832 ?        Ss   18:09   0:00 avahi-daemon: running [lukeSU.local]
luke      1024  0.0  0.2  45248  4752 ?        Ss   18:09   0:00 /lib/systemd/systemd --user
luke      1026  0.0  0.0  63464  1708 ?        S    18:09   0:00 (sd-pam)
luke      1029  0.0  0.2  53532  4636 ?        Ss   18:09   0:00 /sbin/upstart --user
luke      1215  0.0  0.0  39928   280 ?        S    18:09   0:00 upstart-udev-bridge --daemon --user
luke      1221  0.0  0.2  43864  4272 ?        Ss   18:09   0:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-GRGGhjU43e
luke      1235  0.0  0.4  93416  9136 ?        Ss   18:09   0:00 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
luke      1256  0.0  0.3 212256  6760 ?        Sl   18:09   0:00 gnome-keyring-daemon --start --components pkcs11,secrets
luke      1278  0.0  2.3 621892 48940 ?        Ssl  18:09   0:01 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
luke      1280  0.0  0.0 173608   792 ?        Ss   18:09   0:00 gpg-agent --homedir /home/luke/.gnupg --use-standard-socket --daemon
luke      1282  0.0  0.0  39864   328 ?        S    18:09   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
luke      1284  0.0  0.0  39864   328 ?        S    18:09   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
luke      1286  0.0  0.0  48356   400 ?        S    18:09   0:00 upstart-file-bridge --daemon --user
luke      1288  0.2  0.5 365560 10904 ?        Ssl  18:09   0:06 /usr/bin/ibus-daemon --daemonize --xim
luke      1297  0.0  0.3 281592  6520 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfsd
luke      1302  0.0  0.3 419960  7164 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
luke      1308  0.0  0.3 284552  7972 ?        Sl   18:09   0:00 /usr/lib/ibus/ibus-dconf
luke      1312  0.0  1.4 479396 29704 ?        Sl   18:09   0:01 /usr/lib/ibus/ibus-ui-gtk3
luke      1318  0.0  0.5 353668 10264 ?        Sl   18:09   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
luke      1323  0.0  1.1 430352 22708 ?        Sl   18:09   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
luke      1326  0.0  0.2  42900  4116 ?        S    18:09   0:00 /usr/bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
luke      1330  0.0  0.3 206972  6420 ?        Sl   18:09   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
luke      1349  0.0  0.3 208688  7644 ?        Sl   18:09   0:02 /usr/lib/ibus/ibus-engine-simple
luke      1361  0.0  1.8 655200 37668 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/hud/hud-service
luke      1363  0.0  1.6 856000 33568 ?        Ssl  18:09   0:00 /usr/lib/unity-settings-daemon/unity-settings-daemon
luke      1369 12.6  9.3 1251752 191636 ?      Rsl  18:09   5:10 compiz
luke      1372  0.0  0.8 626972 16856 ?        Ssl  18:09   0:00 /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
luke      1377  0.0  1.5 567268 32668 ?        Ssl  18:09   0:01 /usr/lib/x86_64-linux-gnu/unity/unity-panel-service
luke      1387  0.0  0.2 178664  4776 ?        Sl   18:09   0:00 /usr/lib/dconf/dconf-service
luke      1418  0.0  0.4 367268  8644 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
luke      1419  0.0  0.3 356120  7808 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
luke      1422  0.0  0.5 367764 11036 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
luke      1427  0.0  1.0 788888 22016 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
luke      1438  0.0  1.4 659688 29592 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard/indicator-keyboard-service --use-gtk
luke      1439  0.0  0.5 682876 11752 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
luke      1441  0.0  1.2 550168 25224 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
luke      1446  0.0  0.4 643392  8460 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
luke      1449  0.0  1.1 630560 23108 ?        Sl   18:09   0:00 /usr/lib/evolution/evolution-source-registry
luke      1451  0.0  0.7 395940 14536 ?        Ssl  18:09   0:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
luke      1466  0.0  0.5 442008 11276 ?        S<l  18:09   0:00 /usr/bin/pulseaudio --start --log-target=syslog
luke      1535  0.0  3.0 869416 62124 ?        Sl   18:09   0:00 /usr/lib/evolution/evolution-calendar-factory
luke      1550  0.1  2.4 974308 49936 ?        Sl   18:09   0:03 nautilus -n
luke      1551  0.2  6.0 994812 123492 ?       Sl   18:09   0:05 /usr/bin/gnome-software --gapplication-service
luke      1555  0.0  1.0 431960 22384 ?        Sl   18:09   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
luke      1559  0.0  1.6 664852 33024 ?        Sl   18:09   0:00 nm-applet
luke      1564  0.0  1.1 577364 23992 ?        Sl   18:09   0:00 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
luke      1589  0.0  0.4 303444  9716 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
luke      1603  0.0  0.3 278788  7128 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
luke      1610  0.0  0.2 264600  4980 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfs-goa-volume-monitor
luke      1615  0.0  0.4 410684  8984 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
luke      1627  0.0  0.3 266592  6528 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
luke      1633  0.0  2.4 821284 50536 ?        Sl   18:09   0:00 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory contacts --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.Calendarx1535x2 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/Calendar/1535/2
luke      1638  0.0  0.5 370716 10804 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
luke      1653  0.0  2.5 813896 52188 ?        Sl   18:09   0:00 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory local --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.Calendarx1535x3 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/Calendar/1535/3
luke      1658  0.0  0.9 704364 19712 ?        Sl   18:09   0:00 /usr/lib/evolution/evolution-addressbook-factory
luke      1673  0.0  0.9 779856 19248 ?        Sl   18:09   0:00 /usr/lib/evolution/evolution-addressbook-factory-subprocess --factory local --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.AddressBookx1658x2 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/AddressBook/1658/2
luke      1713  0.0  0.2 193048  5436 ?        Sl   18:09   0:00 /usr/lib/gvfs/gvfsd-metadata
luke      1778  0.0  0.7 490732 16040 ?        Sl   18:10   0:00 zeitgeist-datahub
luke      1785  0.0  0.0   4508   704 ?        S    18:10   0:00 /bin/sh -c /usr/lib/x86_64-linux-gnu/zeitgeist/zeitgeist-maybe-vacuum; /usr/bin/zeitgeist-daemon
luke      1789  0.0  0.4 423528  9544 ?        Sl   18:10   0:00 /usr/bin/zeitgeist-daemon
luke      1797  0.0  0.7 321524 15228 ?        Sl   18:10   0:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
luke      1841  0.0  0.4 371136  8388 ?        Sl   18:10   0:00 /usr/lib/gvfs/gvfsd-network --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
luke      1862  0.0  0.3 368792  6732 ?        Sl   18:10   0:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.6 /org/gtk/gvfs/exec_spaw/4
luke      1903  0.0  1.2 599952 25844 ?        Sl   18:10   0:00 update-notifier
luke      1929  0.0  1.3 450572 28556 ?        Sl   18:10   0:00 /usr/lib/x86_64-linux-gnu/notify-osd
luke      1934  0.8  1.9 657716 39264 ?        Sl   18:10   0:20 gedit /home/luke/wats1030-intro-to-unix-master/nix_scavenger_hunt.md
luke      1953  0.0  0.4 522096  8604 ?        Sl   18:11   0:00 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
luke     17673  0.4  1.7 662792 35788 ?        Sl   18:35   0:03 /usr/lib/gnome-terminal/gnome-terminal-server
luke     17680  0.0  0.2  29448  4952 pts/4    Ss   18:35   0:00 bash
luke     17779  0.0  0.8 654052 17000 ?        Sl   18:48   0:00 /usr/lib/x86_64-linux-gnu/unity-scope-home/unity-scope-home
luke     17793  0.1  1.1 656808 24496 ?        Sl   18:48   0:00 /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
luke     17795  0.0  0.6 563928 13056 ?        Sl   18:48   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
luke     17833  0.0  0.1  44432  3388 pts/4    R+   18:50   0:00 ps aux
luke     17834  0.0  0.0  21296   948 pts/4    S+   18:50   0:00 grep --color=auto luke


