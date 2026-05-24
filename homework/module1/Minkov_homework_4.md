Завдання 1:

ddminkov@ddminkov-virtual-machine:~$ sudo apt update
[sudo] password for ddminkov:    
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://security.ubuntu.com/ubuntu noble-security InRelease              
Hit:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease                
Hit:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease              
Ign:5 http://packages.linuxmint.com zena InRelease
Hit:6 http://packages.linuxmint.com zena Release
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
143 packages can be upgraded. Run 'apt list --upgradable' to see them.
ddminkov@ddminkov-virtual-machine:~$ sudo apt install tree -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  tree
0 upgraded, 1 newly installed, 0 to remove and 143 not upgraded.
Need to get 47,4 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 tree amd64 2.1.1-2ubuntu3.24.04.2 [47,4 kB]
Fetched 47,4 kB in 0s (471 kB/s)
Selecting previously unselected package tree.
(Reading database ... 546498 files and directories currently installed.)
Preparing to unpack .../tree_2.1.1-2ubuntu3.24.04.2_amd64.deb ...
Unpacking tree (2.1.1-2ubuntu3.24.04.2) ...
Setting up tree (2.1.1-2ubuntu3.24.04.2) ...
Processing triggers for man-db (2.12.0-4build2) ...
ddminkov@ddminkov-virtual-machine:~$ tree --version
tree v2.1.1 © 1996 - 2023 by Steve Baker, Thomas Moore, Francesc Rocher, Florian Sesser, Kyosuke Tokoro
ddminkov@ddminkov-virtual-machine:~$ sudo apt remove tree -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  tree
0 upgraded, 0 newly installed, 1 to remove and 143 not upgraded.
After this operation, 111 kB disk space will be freed.
(Reading database ... 546505 files and directories currently installed.)
Removing tree (2.1.1-2ubuntu3.24.04.2) ...
Processing triggers for man-db (2.12.0-4build2) ...

Завдання 2:

ddminkov@ddminkov-virtual-machine:~$ sudo systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enab>
     Active: active (running) since Sun 2026-05-24 18:31:17 EEST; 7min ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 5659 (sshd)
      Tasks: 1 (limit: 4533)
     Memory: 1.2M (peak: 1.4M)
        CPU: 18ms
     CGroup: /system.slice/ssh.service
             └─5659 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

May 24 18:31:17 ddminkov-virtual-machine systemd[1]: Starting ssh.service - Op>
May 24 18:31:17 ddminkov-virtual-machine sshd[5659]: Server listening on 0.0.0>
May 24 18:31:17 ddminkov-virtual-machine sshd[5659]: Server listening on :: po>
May 24 18:31:17 ddminkov-virtual-machine systemd[1]: Started ssh.service - Ope>
ddminkov@ddminkov-virtual-machine:~$ sudo systemctl stop ssh
Stopping 'ssh.service', but its triggering units are still active:
ssh.socket
ddminkov@ddminkov-virtual-machine:~$ sudo systemctl status ssh
○ ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enab>
     Active: inactive (dead) since Sun 2026-05-24 18:38:54 EEST; 2s ago
   Duration: 7min 36.571s
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 5659 ExecStart=/usr/sbin/sshd -D $SSHD_OPTS (code=exited, status=0>
   Main PID: 5659 (code=exited, status=0/SUCCESS)
        CPU: 19ms

May 24 18:31:17 ddminkov-virtual-machine systemd[1]: Starting ssh.service - Op>
May 24 18:31:17 ddminkov-virtual-machine sshd[5659]: Server listening on 0.0.0>
May 24 18:31:17 ddminkov-virtual-machine sshd[5659]: Server listening on :: po>
May 24 18:31:17 ddminkov-virtual-machine systemd[1]: Started ssh.service - Ope>
May 24 18:38:54 ddminkov-virtual-machine systemd[1]: Stopping ssh.service - Op>
May 24 18:38:54 ddminkov-virtual-machine systemd[1]: ssh.service: Deactivated >
May 24 18:38:54 ddminkov-virtual-machine sshd[5659]: Received signal 15; termi>
May 24 18:38:54 ddminkov-virtual-machine systemd[1]: Stopped ssh.service - Ope>
ddminkov@ddminkov-virtual-machine:~$ sudo systemctl start ssh
ddminkov@ddminkov-virtual-machine:~$ sudo systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enab>
     Active: active (running) since Sun 2026-05-24 18:39:11 EEST; 2s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 6544 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 6545 (sshd)
      Tasks: 1 (limit: 4533)
     Memory: 1.2M (peak: 1.5M)
        CPU: 19ms
     CGroup: /system.slice/ssh.service
             └─6545 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

May 24 18:39:11 ddminkov-virtual-machine systemd[1]: Starting ssh.service - Op>
May 24 18:39:11 ddminkov-virtual-machine sshd[6545]: Server listening on 0.0.0>
May 24 18:39:11 ddminkov-virtual-machine sshd[6545]: Server listening on :: po>
May 24 18:39:11 ddminkov-virtual-machine systemd[1]: Started ssh.service - Ope>
ddminkov@ddminkov-virtual-machine:~$ sudo systemctl enable ssh
Synchronizing state of ssh.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable ssh

Завдання 3:

ddminkov@ddminkov-virtual-machine:~$ cd /var/log
tail -n 10 syslog
2026-05-24T18:39:11.270126+03:00 ddminkov-virtual-machine systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
2026-05-24T18:39:24.626296+03:00 ddminkov-virtual-machine systemd[1]: Reloading requested from client PID 6558 ('systemctl') (unit session-c1.scope)...
2026-05-24T18:39:24.626461+03:00 ddminkov-virtual-machine systemd[1]: Reloading...
2026-05-24T18:39:24.830148+03:00 ddminkov-virtual-machine systemd[1]: Reloading finished in 203 ms.
2026-05-24T18:39:24.887074+03:00 ddminkov-virtual-machine systemd[1]: Reloading requested from client PID 6648 ('systemctl') (unit session-c1.scope)...
2026-05-24T18:39:24.887198+03:00 ddminkov-virtual-machine systemd[1]: Reloading...
2026-05-24T18:39:25.082263+03:00 ddminkov-virtual-machine systemd[1]: Reloading finished in 194 ms.
2026-05-24T18:39:25.109809+03:00 ddminkov-virtual-machine systemd[1]: Reloading requested from client PID 6554 ('systemctl') (unit session-c1.scope)...
2026-05-24T18:39:25.109896+03:00 ddminkov-virtual-machine systemd[1]: Reloading...
2026-05-24T18:39:25.303609+03:00 ddminkov-virtual-machine systemd[1]: Reloading finished in 193 ms.
ddminkov@ddminkov-virtual-machine:/var/log$ sudo journalctl -p err
Mar 28 13:46:47 ddminkov-virtual-machine kernel: piix4_smbus 0000:00:07.3: SMB>
Mar 28 13:46:48 ddminkov-virtual-machine kernel: Bluetooth: hci0: unexpected c>
Mar 28 13:46:48 ddminkov-virtual-machine kernel: Bluetooth: hci0: Opcode 0x0c1>
Mar 28 13:46:56 ddminkov-virtual-machine systemd[1]: Failed to start casper-md>
Mar 28 13:48:19 ddminkov-virtual-machine systemd-coredump[2169]: [🡕] Process 1>
                                                                  
                                                                  Module libude>
                                                                  Module libzst>
                                                                  Module libgcc>
                                                                  Module libstd>
                                                                  Module libsys>
                                                                  Module libato>
                                                                  Stack trace o>
                                                                  #0  0x00007c7>
                                                                  #1  0x00007c7>
                                                                  #2  0x00007c7>
                                                                  #3  0x00007c7>
                                                                  #4  0x00007c7>
                                                                  #5  0x00007c7>
                                                                  #6  0x00007c7>
                                                                  #7  0x00007c7>
                                                                  #8  0x00007c7>
                                                                  #9  0x00007c7>
ddminkov@ddminkov-virtual-machine:/var/log$ sudo journalctl -u ssh | grep -E "Started|Stopped"
May 24 18:31:17 ddminkov-virtual-machine systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
May 24 18:38:54 ddminkov-virtual-machine systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
May 24 18:39:11 ddminkov-virtual-machine systemd[1]: Started ssh.service - OpenBSD Secure Shell server.

Завдання 4:

ddminkov@ddminkov-virtual-machine:/var/log$ nano ~/my_date_script.sh
  GNU nano 7.2                     /home/ddminkov/my_date_script.sh                               
#!/bin/bash
while true
do
  date >> /tmp/my_date_output.txt
  sleep 1
done

ddminkov@ddminkov-virtual-machine:/var/log$ chmod +x ~/my_date_script.sh
ddminkov@ddminkov-virtual-machine:/var/log$ sudo nano /etc/systemd/system/myscript.service
  GNU nano 7.2                                  /etc/systemd/system/myscript.service                                            
[Unit]
Description=My Custom Date Logging Service
After=network.target

[Service]
Type=simple
ExecStart=/home/ddminkov/my_date_script.sh
Restart=on-failure

[Install]
WantedBy=multi-user.target

ddminkov@ddminkov-virtual-machine:/var/log$ sudo systemctl daemon-reload
ddminkov@ddminkov-virtual-machine:/var/log$ sudo systemctl start myscript.service
ddminkov@ddminkov-virtual-machine:/var/log$ sudo systemctl status myscript.service
● myscript.service - My Custom Date Logging Service
     Loaded: loaded (/etc/systemd/system/myscript.service; disabled; preset: enabled)
     Active: active (running) since Sun 2026-05-24 18:48:52 EEST; 3s ago
   Main PID: 7078 (my_date_script.)
      Tasks: 2 (limit: 4533)
     Memory: 880.0K (peak: 1.2M)
        CPU: 8ms
     CGroup: /system.slice/myscript.service
             ├─7078 /bin/bash /home/ddminkov/my_date_script.sh
             └─7086 sleep 1

May 24 18:48:52 ddminkov-virtual-machine systemd[1]: Started myscript.service - My Custom Date Logging Service.
ddminkov@ddminkov-virtual-machine:/var/log$ tail -f /tmp/my_date_output.txt
Sun May 24 06:49:11 PM EEST 2026
Sun May 24 06:49:12 PM EEST 2026
Sun May 24 06:49:13 PM EEST 2026
Sun May 24 06:49:14 PM EEST 2026
Sun May 24 06:49:15 PM EEST 2026
Sun May 24 06:49:16 PM EEST 2026
Sun May 24 06:49:17 PM EEST 2026
Sun May 24 06:49:18 PM EEST 2026
Sun May 24 06:49:19 PM EEST 2026
Sun May 24 06:49:20 PM EEST 2026
Sun May 24 06:49:21 PM EEST 2026
Sun May 24 06:49:22 PM EEST 2026
Sun May 24 06:49:23 PM EEST 2026
Sun May 24 06:49:24 PM EEST 2026
Sun May 24 06:49:25 PM EEST 2026
Sun May 24 06:49:26 PM EEST 2026
qSun May 24 06:49:27 PM EEST 2026
Sun May 24 06:49:28 PM EEST 2026
Sun May 24 06:49:29 PM EEST 2026
^C
ddminkov@ddminkov-virtual-machine:/var/log$ sudo systemctl stop myscript.service
ddminkov@ddminkov-virtual-machine:/var/log$ sudo systemctl status myscript.service
○ myscript.service - My Custom Date Logging Service
     Loaded: loaded (/etc/systemd/system/myscript.service; disabled; preset: enabled)
     Active: inactive (dead)

May 24 18:46:06 ddminkov-virtual-machine systemd[1]: myscript.service: Main process exited, code=exited, status=203/EXEC
May 24 18:46:06 ddminkov-virtual-machine systemd[1]: myscript.service: Failed with result 'exit-code'.
May 24 18:46:06 ddminkov-virtual-machine systemd[1]: myscript.service: Scheduled restart job, restart counter is at 5.
May 24 18:46:06 ddminkov-virtual-machine systemd[1]: myscript.service: Start request repeated too quickly.
May 24 18:46:06 ddminkov-virtual-machine systemd[1]: myscript.service: Failed with result 'exit-code'.
May 24 18:46:06 ddminkov-virtual-machine systemd[1]: Failed to start myscript.service - My Custom Date Logging Service.
May 24 18:48:52 ddminkov-virtual-machine systemd[1]: Started myscript.service - My Custom Date Logging Service.
May 24 18:49:43 ddminkov-virtual-machine systemd[1]: Stopping myscript.service - My Custom Date Logging Service...
May 24 18:49:43 ddminkov-virtual-machine systemd[1]: myscript.service: Deactivated successfully.
May 24 18:49:43 ddminkov-virtual-machine systemd[1]: Stopped myscript.service - My Custom Date Logging Service.
ddminkov@ddminkov-virtual-machine:/var/log$ tail -f /tmp/my_date_output.txt
Sun May 24 06:49:33 PM EEST 2026
Sun May 24 06:49:34 PM EEST 2026
Sun May 24 06:49:35 PM EEST 2026
Sun May 24 06:49:36 PM EEST 2026
Sun May 24 06:49:37 PM EEST 2026
Sun May 24 06:49:38 PM EEST 2026
Sun May 24 06:49:39 PM EEST 2026
Sun May 24 06:49:40 PM EEST 2026
Sun May 24 06:49:41 PM EEST 2026
Sun May 24 06:49:42 PM EEST 2026
^C
