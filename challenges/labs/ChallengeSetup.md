AWS LIST

Name : HendrickInstance1
Instance ID: i-0ea6af834ec154275
Public DNS IPV4: ec2-54-169-33-58.ap-southeast-1.compute.amazonaws.com
IPV4 Public IP: 54.169.33.58
key Name: awsKeyPair2

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

[centos@ip-172-31-29-233 ~]$ sudo su root
[root@ip-172-31-29-233 centos]# useradd -u 2700 purnama
[root@ip-172-31-29-233 centos]# useradd -u 2800 basuki
[root@ip-172-31-29-233 centos]# 
```

----------------------------------------------------------------------------------------------------------------------------------------------------------------------

Name : HendrickInstance2
Instance ID: i-06ffe80ed7dc97714
Public DNS IPV4: ec2-3-0-145-67.ap-southeast-1.compute.amazonaws.com
IPV4 Public IP: 3.0.145.67
key Name: awsKeyPair3

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
[centos@ip-172-31-26-169 ~]$ sudo useradd -u 2700 purnama
[centos@ip-172-31-26-169 ~]$ sudo useradd -u 2800 basuki
[centos@ip-172-31-26-169 ~]$ 


----------------------------------------------------------------------------------------------------------------------------------------------------------------------

Name : HendrickInstance3
Instance ID: i-0d36fd715c996643b
Public DNS IPV4: ec2-54-169-159-1.ap-southeast-1.compute.amazonaws.com
IPV4 Public IP: 54.169.159.1
key Name: awsKeyPair4

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


[centos@ip-172-31-17-15 ~]$ sudo useradd -u 2700 purnama
[centos@ip-172-31-17-15 ~]$ sudo useradd -u 2800 basuki
[centos@ip-172-31-17-15 ~]$ ^C
[centos@ip-172-31-17-15 ~]$ 
 


