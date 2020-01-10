[centos@ip-172-31-29-233 ~]$ mysql --version
mysql  Ver 14.14 Distrib 5.6.46, for Linux (x86_64) using  EditLine wrapper
[centos@ip-172-31-29-233 ~]$ sudo systemctl start mysqld
[centos@ip-172-31-29-233 ~]$ sudo systemctl status -l mysqld
● mysqld.service - MySQL Community Server
   Loaded: loaded (/usr/lib/systemd/system/mysqld.service; enabled; vendor preset: disabled)
   Active: active (running) since Jum 2020-01-10 10:08:31 UTC; 7s ago
  Process: 15106 ExecStartPost=/usr/bin/mysql-systemd-start post (code=exited, status=0/SUCCESS)
  Process: 15039 ExecStartPre=/usr/bin/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 15105 (mysqld_safe)
   CGroup: /system.slice/mysqld.service
           ├─15105 /bin/sh /usr/bin/mysqld_safe --basedir=/usr
           └─15271 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib64/mysql/plugin --log-error=/var/log/mysqld.log --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/lib/mysql/mysql.sock

Jan 10 10:08:28 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: 2020-01-10 10:08:28 15080 [Note] InnoDB: Starting shutdown...
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: 2020-01-10 10:08:30 15080 [Note] InnoDB: Shutdown completed; log sequence number 1625987
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: To do so, start the server, then issue the following commands:
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: /usr/bin/mysqladmin -u root password 'new-password'
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: /usr/bin/mysqladmin -u root -h ip-172-31-29-233.ap-southeast-1.compute.internal password 'new-password'
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysql-systemd-start[15039]: Alternatively you can run:
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysqld_safe[15105]: 200110 10:08:30 mysqld_safe Logging to '/var/log/mysqld.log'.
Jan 10 10:08:30 ip-172-31-29-233.ap-southeast-1.compute.internal mysqld_safe[15105]: 200110 10:08:30 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
Jan 10 10:08:31 ip-172-31-29-233.ap-southeast-1.compute.internal systemd[1]: Started MySQL Community Server.
[centos@ip-172-31-29-233 ~]$ 

[centos@ip-172-31-29-233 ~]$ sudo /usr/bin/mysql_secure_installation 



NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
ERROR 1008 (HY000) at line 1: Can't drop database 'test'; database doesn't exist
 ... Failed!  Not critical, keep moving...
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!




All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!


Cleaning up...
[centos@ip-172-31-29-233 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 14
Server version: 5.6.46 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database scm default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on scm.* to 'scm'@'%'identified by 'scm123'
    -> Ctrl-C -- exit!
Aborted
[centos@ip-172-31-29-233 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 5.6.46 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> grant all on scm.* to 'scm'@'%' identified by 'scm123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database amon default character set utf8 default collate utf8_general_cil
    -> ^DBye
[centos@ip-172-31-29-233 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 5.6.46 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database amon default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on amon.* to 'amon'@'%' identified by 'amon123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database rman default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on rman.* to 'rman'@'%' identified by 'rman123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database hue default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on hue.* to 'hue'@'%' identified by 'hue123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database metastore default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on metastore.* to 'hive'@'%' identified by 'hive123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database sentry default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on sentry.* to 'sentry'@'%' identified by 'sentry123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database nav default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> gramt all on nav.* to 'nav'@'%' identified by 'nav123';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'gramt all on nav.* to 'nav'@'%' identified by 'nav123'' at line 1
mysql> grant all on nav.* to 'nav'@'%' identified by 'nav123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database navms default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on navms.* to 'navms'@'%' identified by 'navms123';
Query OK, 0 rows affected (0,00 sec)

mysql> create database oozie default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0,00 sec)

mysql> grant all on oozie.* to 'oozie'@'%' identified by 'oozie123';
Query OK, 0 rows affected (0,00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| amon               |
| hue                |
| metastore          |
| mysql              |
| nav                |
| navms              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
12 rows in set (0,00 sec)

mysql> show grants for 'scm'@'%'
    -> Ctrl-C -- exit!
Aborted
[centos@ip-172-31-29-233 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 17
Server version: 5.6.46 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show grants for 'scm'@'%';
+----------------------------------------------------------------------------------------------------+
| Grants for scm@%                                                                                   |
+----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'scm'@'%' IDENTIFIED BY PASSWORD '*9265BD0AFF3F2A09ACF8A2E6547B587D580DC3DE' |
| GRANT ALL PRIVILEGES ON `scm`.* TO 'scm'@'%'                                                       |
+----------------------------------------------------------------------------------------------------+
2 rows in set (0,00 sec)

mysql> show grants for 'amon'@'%';
+-----------------------------------------------------------------------------------------------------+
| Grants for amon@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'amon'@'%' IDENTIFIED BY PASSWORD '*6BF4695BC81BDB0AF03A6FC93E8170FD211003A3' |
| GRANT ALL PRIVILEGES ON `amon`.* TO 'amon'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0,00 sec)

mysql> 

