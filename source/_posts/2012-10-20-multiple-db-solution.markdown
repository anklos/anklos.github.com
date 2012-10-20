---
layout: post
title: "'multiple db solution'"
date: 2012-10-20 12:14
comments: true
categories: technical
---

Recently I have been working on a big legacy code base which involves several db schemas. For whatever reasons, great ancestor devs didn't seperate the test and developement database for the project, instead, just used the same databases and tables. As a young and passionate dev, I know this has to be changed. So I decided to setup multiple databases on my machine for running and testing the project.

First, I came across this idea: just install another mysql (we use mysql) db in the virtual machine and it should work straightforward. I used vagrant to do this. A few gotchas here:

1. in /etc/hosts.allow：add `mysqld: ALL : ALLOW` and `mysqld-max: ALL : ALLOW`
2. in /etc/mysql/my.cnf: comment the line `skip-external-locking`, and set `bind-address` to be 0.0.0.0
3. log into mysql, `GRANT ALL ON *.* to 'root'@'%'`

Allright, thats it. But it looks a bit heavy to have a virtual machine running on the backround to just serve as a database.

OK. There should be a smarter way. I did a bit search and found that mysql can have databases in different process and store the data in different folder. That's awesome.

To get the idea about the setup config, simply run `mysqld_multi --example` to get a sample settings, which can be used in /etc/my.cnf. Then initialise the db by doing `/mysql/bin/mysql_install_db --datadir=/data/mysql/data1 --user`. Now there is a very important step which often mssing from most tutorials is before you want to use mysqld_multi to start a mysql instance, you would better start that instance mannualy `mysql.server --basedir --port` and run mysql_upgrdate to make sure there is no error in the newly created mysqld[i]. It is quite often to see some issues solved by this upgrade. After that, you can start a new mysqld by `mysqld_multi start 2`. If it still fails to start mysql, check the error log, which can be set in the my.cnf.

Here is a sample setting:

```
[mysqld_multi]
mysqld     = /usr/local/Cellar/mysql/5.5.27/bin/mysqld_safe
mysqladmin = /usr/local/Cellar/mysql/5.5.27/bin/mysqladmin

[mysqld2]
socket     = /tmp/mysql.sock2
port       = 3307
pid-file   = /usr/local/var/mysql2/mysql.pid2
datadir    = /usr/local/var/mysql2
log-error  = /var/log/mysqld2.log
ft_min_word_len=1
ft_stopword_file = ''
default-storage-engine=InnoDB
```
