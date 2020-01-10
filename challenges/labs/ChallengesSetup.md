AWS LIST

## Instance List

|Instance Name | Instance ID | Public DNS IPV4 | IPV4 Public IP | key Name | OS |
|----------|----------|----------|----------|----------|----------|
|HendrickInstance1| i-0ea6af834ec154275 | ec2-54-169-33-58.ap-southeast-1.compute.amazonaws.com | 54.169.33.58 | awsKeyPair2 | CentOS 7|
|HendrickInstance2| i-06ffe80ed7dc97714 | ec2-3-0-145-67.ap-southeast-1.compute.amazonaws.com | 3.0.145.67 | awsKeyPair3 | CentOS 7|
|HendrickInstance3| i-0d36fd715c996643b | ec2-54-169-159-1.ap-southeast-1.compute.amazonaws.com| 54.169.159.1 | awsKeyPair4 | CentOS 7|

## Connect to SSH And disk Check
```
(base) hendrick@hendrick-ThinkPad-T460:~/Downloads$ ssh -i awsKeyPair2.pem centos@ec2-54-169-33-58.ap-southeast-1.compute.amazonaws.com
The authenticity of host 'ec2-54-169-33-58.ap-southeast-1.compute.amazonaws.com (54.169.33.58)' can't be established.
ECDSA key fingerprint is SHA256:YBkpG3/A/BfVVox6nLlyx5VIIuaFhJwoOPkaHjQ7wro.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'ec2-54-169-33-58.ap-southeast-1.compute.amazonaws.com,54.169.33.58' (ECDSA) to the list of known hosts.
Last login: Fri Jan 10 04:43:36 2020 from 182.0.168.174
[centos@ip-172-31-29-233 ~]$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G  969M   30G   4% /
devtmpfs        7,8G     0  7,8G   0% /dev
tmpfs           7,8G     0  7,8G   0% /dev/shm
tmpfs           7,8G   17M  7,8G   1% /run
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
tmpfs           1,6G     0  1,6G   0% /run/user/0
tmpfs           1,6G     0  1,6G   0% /run/user/1000
```

## Yum Repo List
```
[centos@ip-172-31-29-233 ~]$ sudo yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.usonyx.net
 * extras: centos.usonyx.net
 * updates: centos.usonyx.net
repo id                                                                    repo name                                                                    status
base/7/x86_64                                                              CentOS-7 - Base                                                              10.097
extras/7/x86_64                                                            CentOS-7 - Extras                                                               307
updates/7/x86_64                                                           CentOS-7 - Updates                                                            1.010
repolist: 11.414
```

##User add
```
[centos@ip-172-31-29-233 ~]$ sudo su root
[root@ip-172-31-29-233 centos]# useradd -u 2700 purnama
[root@ip-172-31-29-233 centos]# useradd -u 2800 basuki
[root@ip-172-31-29-233 centos]# 
```

##Add User to Group
```
[centos@ip-172-31-29-233 ~]$ sudo groupadd hackers
[centos@ip-172-31-29-233 ~]$ sudo usermod -a -G hackers basuki
[centos@ip-172-31-29-233 ~]$ sudo usermod -a -G crackers purnama
usermod: group 'crackers' does not exist
[centos@ip-172-31-29-233 ~]$ sudo groupadd crackers
[centos@ip-172-31-29-233 ~]$ sudo usermod -a -G crackers purnama
[centos@ip-172-31-29-233 ~]$ 
```

##User in the group
```
[centos@ip-172-31-26-169 ~]$ su - basuki
Password: 
Last failed login: Jum Jan 10 07:50:20 UTC 2020 on pts/0
There was 1 failed login attempt since the last successful login.
[basuki@ip-172-31-26-169 ~]$ groups
basuki hackers
[basuki@ip-172-31-26-169 ~]$ su - purnama
Password: 
[purnama@ip-172-31-26-169 ~]$ groups
purnama crackers

```

##List /etc/passwd
```
[centos@ip-172-31-29-233 ~]$ sudo cat /etc/passwd | grep basuki
basuki:x:2800:2800::/home/basuki:/bin/bash
[centos@ip-172-31-29-233 ~]$ sudo cat /etc/passwd | grep purnama
purnama:x:2700:2700::/home/purnama:/bin/bash

```

##List /etc/group
```
[centos@ip-172-31-29-233 ~]$ sudo cat /etc/group | grep hackers
hackers:x:2801:basuki
[centos@ip-172-31-29-233 ~]$ sudo cat /etc/group | grep crackers
crackers:x:2802:purnama

```

----------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Connect to SSH and disk Check
```
(base) hendrick@hendrick-ThinkPad-T460:~/Downloads$ ssh -i awsKeyPair3.pem centos@ec2-3-0-145-67.ap-southeast-1.compute.amazonaws.com
The authenticity of host 'ec2-3-0-145-67.ap-southeast-1.compute.amazonaws.com (3.0.145.67)' can't be established.
ECDSA key fingerprint is SHA256:b1lm7QXDZ1ohr1oGfTu70KIR0T5U/Lgkyo+aATKy7UA.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'ec2-3-0-145-67.ap-southeast-1.compute.amazonaws.com,3.0.145.67' (ECDSA) to the list of known hosts.
[centos@ip-172-31-26-169 ~]$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G  896M   30G   3% /
devtmpfs        7,8G     0  7,8G   0% /dev
tmpfs           7,8G     0  7,8G   0% /dev/shm
tmpfs           7,8G   17M  7,8G   1% /run
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
tmpfs           1,6G     0  1,6G   0% /run/user/0
tmpfs           1,6G     0  1,6G   0% /run/user/1000
```

## Yum RepoList 
```
[centos@ip-172-31-26-169 ~]$ sudo yum repolist enabled
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: centos.usonyx.net
 * extras: centos.usonyx.net
 * updates: centos.usonyx.net
base                                                                                                                                   | 3.6 kB  00:00:00     
extras                                                                                                                                 | 2.9 kB  00:00:00     
updates                                                                                                                                | 2.9 kB  00:00:00     
(1/4): base/7/x86_64/group_gz                                                                                                          | 165 kB  00:00:00     
(2/4): extras/7/x86_64/primary_db                                                                                                      | 153 kB  00:00:00     
(3/4): updates/7/x86_64/primary_db                                                                                                     | 5.9 MB  00:00:00     
(4/4): base/7/x86_64/primary_db                                                                                                        | 6.0 MB  00:00:00     
repo id                                                                    repo name                                                                    status
base/7/x86_64                                                              CentOS-7 - Base                                                              10.097
extras/7/x86_64                                                            CentOS-7 - Extras                                                               307
updates/7/x86_64                                                           CentOS-7 - Updates                                                            1.010
repolist: 11.414
```

## User add 
```
[centos@ip-172-31-26-169 ~]$ sudo useradd -u 2700 purnama
[centos@ip-172-31-26-169 ~]$ sudo useradd -u 2800 basuki
[centos@ip-172-31-26-169 ~]$ 
```

##User in the group
```
[centos@ip-172-31-26-169 ~]$ su - basuki
Password: 
Last failed login: Jum Jan 10 07:50:20 UTC 2020 on pts/0
There was 1 failed login attempt since the last successful login.
[basuki@ip-172-31-26-169 ~]$ groups
basuki hackers
[basuki@ip-172-31-26-169 ~]$ su - purnama
Password: 
[purnama@ip-172-31-26-169 ~]$ groups
purnama crackers

```

##List /etc/passwd
```
[centos@ip-172-31-26-169 ~]$ sudo cat /etc/passwd | grep basuki
basuki:x:2800:2800::/home/basuki:/bin/bash
[centos@ip-172-31-26-169 ~]$ sudo cat /etc/passwd | grep purnama
purnama:x:2700:2700::/home/purnama:/bin/bash
[centos@ip-172-31-26-169 ~]$ 
```

##List /etc/group
```
[centos@ip-172-31-26-169 ~]$ sudo cat /etc/group | grep hackers
hackers:x:2801:basuki
[centos@ip-172-31-26-169 ~]$ sudo cat /etc/group | grep crackers
crackers:x:2802:purnama
```


----------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Connect to SSH and disk check
```
(base) hendrick@hendrick-ThinkPad-T460:~/Downloads$ ssh -i awsKeyPair4.pem centos@ec2-54-169-159-1.ap-southeast-1.compute.amazonaws.com
[centos@ip-172-31-17-15 ~]$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       30G  896M   30G   3% /
devtmpfs        7,8G     0  7,8G   0% /dev
tmpfs           7,8G     0  7,8G   0% /dev/shm
tmpfs           7,8G   17M  7,8G   1% /run
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
tmpfs           1,6G     0  1,6G   0% /run/user/1000
tmpfs           1,6G     0  1,6G   0% /run/user/0
```

## Yum repo List
```
[centos@ip-172-31-17-15 ~]$ sudo yum repolist enabled
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: mirror.newmediaexpress.com
 * extras: mirror.newmediaexpress.com
 * updates: mirror.newmediaexpress.com
base                                                     | 3.6 kB     00:00     
extras                                                   | 2.9 kB     00:00     
updates                                                  | 2.9 kB     00:00     
(1/4): base/7/x86_64/group_gz                              | 165 kB   00:00     
(2/4): extras/7/x86_64/primary_db                          | 153 kB   00:00     
(3/4): updates/7/x86_64/primary_db                         | 5.9 MB   00:00     
(4/4): base/7/x86_64/primary_db                            | 6.0 MB   00:00     
repo id                             repo name                             status
base/7/x86_64                       CentOS-7 - Base                       10.097
extras/7/x86_64                     CentOS-7 - Extras                        307
updates/7/x86_64                    CentOS-7 - Updates                     1.010
repolist: 11.414
```

##User add
```
[centos@ip-172-31-17-15 ~]$ sudo useradd -u 2700 purnama
[centos@ip-172-31-17-15 ~]$ sudo useradd -u 2800 basuki
[centos@ip-172-31-17-15 ~]$ ^C
[centos@ip-172-31-17-15 ~]$ 
``` 

##Add User to Group
```
[centos@ip-172-31-17-15 ~]$ sudo groupadd hackers
[centos@ip-172-31-17-15 ~]$ sudo groupadd crackers
[centos@ip-172-31-17-15 ~]$ sudo usermod -aG hackers basuki
[centos@ip-172-31-17-15 ~]$ sudo usermod -aG crackers purnama
```

##User In the Group
```
[centos@ip-172-31-17-15 ~]$ groups basuki
basuki : basuki hackers
[centos@ip-172-31-17-15 ~]$ groups purnama
purnama : purnama crackers

```

##List /etc/passwd
```
[centos@ip-172-31-17-15 ~]$ sudo cat /etc/passwd | grep purnama
purnama:x:2700:2700::/home/purnama:/bin/bash
[centos@ip-172-31-17-15 ~]$ sudo cat /etc/passwd | grep basuki
basuki:x:2800:2800::/home/basuki:/bin/bash
```

##List /etc/group
```
[centos@ip-172-31-17-15 ~]$ sudo cat /etc/group | grep hackers
hackers:x:2801:basuki
[centos@ip-172-31-17-15 ~]$ sudo cat /etc/group | grep crackers
crackers:x:2802:purnama

```

