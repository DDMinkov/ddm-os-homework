Завдання 1:

ddminkov@ddminkov-virtual-machine:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:79:c6:79 brd ff:ff:ff:ff:ff:ff
    altname enp2s1
    inet 192.168.SECRET/24 brd 192.168.216.255 scope global dynamic noprefixroute ens33
       valid_lft 1786sec preferred_lft 1786sec
    inet6 fe80::2038:2a14:9bc:b96d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
ddminkov@ddminkov-virtual-machine:~$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=128 time=30.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=128 time=41.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=128 time=29.2 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=128 time=28.8 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3009ms
rtt min/avg/max/mdev = 28.786/32.504/41.419/5.190 ms
ddminkov@ddminkov-virtual-machine:~$ ss -tulpn
Netid  State   Recv-Q  Send-Q   Local Address:Port    Peer Address:Port Process 
udp    UNCONN  0       0              0.0.0.0:43734        0.0.0.0:*
udp    UNCONN  0       0              0.0.0.0:5353         0.0.0.0:*
udp    UNCONN  0       0           127.0.0.54:53           0.0.0.0:*
udp    UNCONN  0       0        127.0.0.53%lo:53           0.0.0.0:*
udp    UNCONN  0       0                 [::]:5353            [::]:*
udp    UNCONN  0       0                 [::]:51504           [::]:*
tcp    LISTEN  0       4096        127.0.0.54:53           0.0.0.0:*
tcp    LISTEN  0       4096           0.0.0.0:22           0.0.0.0:*
tcp    LISTEN  0       4096     127.0.0.53%lo:53           0.0.0.0:*
tcp    LISTEN  0       4096         127.0.0.1:631          0.0.0.0:*
tcp    LISTEN  0       4096             [::1]:631             [::]:*
tcp    LISTEN  0       4096              [::]:22              [::]:*

Завдання 2:

ddminkov@ddminkov-virtual-machine:~$ ssh-keygen -t rsa -b 4096
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ddminkov/.ssh/id_rsa): 
Created directory '/home/ddminkov/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/ddminkov/.ssh/id_rsa
Your public key has been saved in /home/ddminkov/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:NcZtbyBp04ev1KqcMlR4E6TRJinWo5UNI6j1PdZD4ew ddminkov@ddminkov-virtual-machine
The key's randomart image is:
+---[RSA 4096]----+
|     ...+Bo.     |
|    o o.BB*+ .   |
|   o o =.B%.* .  |
|  .   o ==*= *   |
|       .S+Eo. =  |
|        .  . +   |
|       .    o    |
|        o. o     |
|         o+      |
+----[SHA256]-----+
ddminkov@ddminkov-virtual-machine:~$ ssh-copy-id ddminkov@192.168.SECRET
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
ddminkov@192.168.SECRET's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'ddminkov@192.168.SECRET'"
and check to make sure that only the key(s) you wanted were added.

ddminkov@ddminkov-virtual-machine:~$ nano ~/.ssh/config
  GNU nano 7.2               /home/ddminkov/.ssh/config *
Host myserver
    HostName 192.168.SECRET
    User ddminkov
    IdentityFile ~/.ssh/id_rsa
ddminkov@ddminkov-virtual-machine:~$ ssh myserver

ddminkov@ddminkov-virtual-machine:~$ exit
logout
Connection to 192.168.SECRET closed.

Завдання 3:

ddminkov@ddminkov-virtual-machine:~$ echo "test" > test.txt
ddminkov@ddminkov-virtual-machine:~$ scp test.txt myserver:~/
test.txt                                      100%    5    16.1KB/s   00:00    
ddminkov@ddminkov-virtual-machine:~$ ssh myserver "mkdir -p ~/sync_folder"
ddminkov@ddminkov-virtual-machine:~$ mkdir -p ~/local_sync && echo "rsync test" > ~/local_sync/file.txt
rsync -avz ~/local_sync/ myserver:~/sync_folder/
sending incremental file list
./
file.txt

sent 151 bytes  received 38 bytes  378,00 bytes/sec
total size is 11  speedup is 0,06
ddminkov@ddminkov-virtual-machine:~$ sftp myserver
Connected to myserver.
sftp> ls -l
drwxr-xr-x    ? ddminkov ddminkov     4096 Jun  3 12:17 Desktop
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 13:47 Documents
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 14:28 Downloads
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 13:47 Music
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 19:09 Pictures
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 13:47 Public
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 13:47 Templates
drwxr-xr-x    ? ddminkov ddminkov     4096 Mar 28 13:47 Videos
drwxrwxr-x    ? ddminkov ddminkov     4096 Apr 12 18:33 homwurk_foldr
drwxrwxr-x    ? ddminkov ddminkov     4096 Jun  3 12:19 local_sync
-rwxrwxr-x    ? ddminkov ddminkov       76 May 24 18:35 my_date_script.sh
-rw-------    ? ddminkov ddminkov        0 May  1 16:32 nohup.out
drwxrwxr-x    ? ddminkov ddminkov     4096 Jun  3 12:19 sync_folder
-rw-rw-r--    ? ddminkov ddminkov        5 Jun  3 12:19 test.txt
sftp> cd sync_folder
sftp> ls -l
-rw-rw-r--    ? ddminkov ddminkov       11 Jun  3 12:19 file.txt
sftp> bye
