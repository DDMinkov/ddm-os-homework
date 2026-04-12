Завдання 1:

ddminkov@ddminkov-virtual-machine:~$ cd /
ddminkov@ddminkov-virtual-machine:/$ ls
bin                etc                lost+found  root                swapfile
bin.usr-is-merged  home               media       run                 sys
boot               lib                mnt         sbin                tmp
cdrom              lib64              opt         sbin.usr-is-merged  usr
dev                lib.usr-is-merged  proc        srv                 var
ddminkov@ddminkov-virtual-machine:/$ cd /etc
ddminkov@ddminkov-virtual-machine:/etc$ ls
adduser.conf            hostname              pm
adjtime                 hosts                 pnm2ppa.conf
alsa                    hosts.allow           polkit-1
alternatives            hosts.deny            ppp
anacrontab              hp                    profile
apg.conf                ifplugd               profile.d
apm                     ImageMagick-6         protocols
apparmor                init                  pulse
apparmor.d              init.d                python3
apt                     initramfs-tools       python3.12
avahi                   inputrc               rc0.d
bash.bashrc             inxi.conf             rc1.d
bash_completion         ipp-usb               rc2.d
bash_completion.d       iproute2              rc3.d
bindresvport.blacklist  issue                 rc4.d
binfmt.d                issue.net             rc5.d
bluetooth               kernel                rc6.d
brlapi.key              kerneloops.conf       rcS.d
brltty                  keyutils              request-key.conf
brltty.conf             ld.so.cache           request-key.d
ca-certificates         ld.so.conf            resolv.conf
ca-certificates.conf    ld.so.conf.d          rmt
casper.conf             legal                 rpc
chatscripts             libao.conf            rsyslog.conf
cifs-utils              libaudit.conf         rsyslog.d
compizconfig            libblockdev           samba
console-setup           libnl-3               sane.d
cracklib                libpaper.d            security
credstore               libreoffice           selinux
credstore.encrypted     lightdm               sensors3.conf
cron.d                  linuxmint             sensors.d
cron.daily              locale.alias          services
cron.hourly             locale.conf           sgml
cron.monthly            locale.gen            shadow
crontab                 localtime             shadow-
cron.weekly             logcheck              shells
cron.yearly             login.defs            skel
cryptsetup-initramfs    logrotate.conf        snmp
cups                    logrotate.d           sound
cupshelpers             lsb-release           speech-dispatcher
dbus-1                  ltrace.conf           ssh
dconf                   lvm                   ssl
debconf.conf            machine-id            subgid
debian_version          magic                 subgid-
debuginfod              magic.mime            subuid
default                 mailcap               subuid-
deluser.conf            mailcap.order         sudo.conf
depmod.d                manpath.config        sudoers
dhcp                    mate-settings-daemon  sudoers.d
dhcpcd.conf             mdadm                 sudo_logsrvd.conf
dictionaries-common     menu-methods          supercat
dkms                    mime.types            sysctl.conf
dpkg                    mke2fs.conf           sysctl.d
e2scrub.conf            ModemManager          systemd
emacs                   modprobe.d            terminfo
environment             modules               thermald
environment.d           modules-load.d        timeshift
ethertypes              motd                  timezone
fonts                   mtab                  timidity
fprintd.conf            mtools.conf           tmpfiles.d
fstab                   nanorc                ucf.conf
fuse.conf               netconfig             udev
fwupd                   netplan               udisks2
gai.conf                network               ufw
gdb                     networkd-dispatcher   updatedb.conf
geoclue                 NetworkManager        update-motd.d
ghostscript             networks              UPower
glvnd                   newt                  upstream-release
gnome-app-install       nftables.conf         usb_modeswitch.conf
gnome-system-tools      nsswitch.conf         usb_modeswitch.d
gnutls                  openal                vconsole.conf
gprofng.rc              openni2               vdpau_wrapper.cfg
groff                   openvpn               vim
group                   opt                   vmware-tools
group-                  os-release            vtrgb
grub.d                  PackageKit            vulkan
gshadow                 pam.conf              wgetrc
gshadow-                pam.d                 wpa_supplicant
gss                     papersize             X11
gtk-2.0                 passwd                xattr.conf
gtk-3.0                 passwd-               xdg
guest-session           pcmcia                xml
gufw                    perl                  xrdb
hdparm.conf             pki                   zsh_command_not_found
host.conf               plymouth
ddminkov@ddminkov-virtual-machine:/etc$ cd /home
ddminkov@ddminkov-virtual-machine:/home$ ls
ddminkov

Завдання 2:

ddminkov@ddminkov-virtual-machine:~$ mkdir homwurk_foldr
ddminkov@ddminkov-virtual-machine:~$ touch homwurk_foldr/file.txt
ddminkov@ddminkov-virtual-machine:~$ cp homwurk_foldr/file.txt homwurk_foldr/file_double.txt
ddminkov@ddminkov-virtual-machine:~$ mv homwurk_foldr/file_double.txt homwurk_foldr/file_rename.txt
ddminkov@ddminkov-virtual-machine:~$ ln homwurk_foldr/file.txt homwurk_foldr/file_HARD.txt
ddminkov@ddminkov-virtual-machine:~$ ln -s homwurk_foldr/file.txt homwurk_foldr/file_sowft.txt
ddminkov@ddminkov-virtual-machine:~$ find ~/homwurk_foldr/file.txt
/home/ddminkov/homwurk_foldr/file.txt

Завдання 3:

ddminkov@ddminkov-virtual-machine:~$ ls -l homwurk_foldr/file.txt
-rw-rw-r-- 2 ddminkov ddminkov 0 Apr 12 18:30 homwurk_foldr/file.txt
ddminkov@ddminkov-virtual-machine:~$ chmod 444 homwurk_foldr/file.txt
ddminkov@ddminkov-virtual-machine:~$ chmod u+w homwurk_foldr/file.txt
ddminkov@ddminkov-virtual-machine:~$ umask
0002
ddminkov@ddminkov-virtual-machine:~$ umask 022
ddminkov@ddminkov-virtual-machine:~$ umask
0022

Завдання 4:

ddminkov@ddminkov-virtual-machine:~$ sudo -i
[sudo] password for ddminkov:    
root@ddminkov-virtual-machine:~# sudo adduser testy
info: Adding user `testy' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `testy' (1001) ...
info: Adding new user `testy' (1001) with group `testy (1001)' ...
info: Creating home directory `/home/testy' ...
info: Copying files from `/etc/skel' ...
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for testy
Enter the new value, or press ENTER for the default
	Full Name []: Testy
	Room Number []: 4 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
info: Adding new user `testy' to supplemental / extra groups `users' ...
info: Adding user `testy' to group `users' ...
root@ddminkov-virtual-machine:~# sudo usermod -aG sudo testy
root@ddminkov-virtual-machine:~# grep "Testy"
   
^Z
[1]+  Stopped                 grep --color=auto "Testy"
root@ddminkov-virtual-machine:~# grep "Testy" /etc/passwd
testy:x:1001:1001:Testy,4,,:/home/testy:/bin/bash
root@ddminkov-virtual-machine:~# sudo deluser testy
info: Removing crontab ...
info: Removing user `testy' ...
