﻿# kafka-stream
https://docs.oracle.com/en/learn/use_dnf_on_oracle_8/#list-package-information

available packages:
sudo dnf list jdk*

Update package repository:
---
sudo dnf update

Install JDK:
--
sudo dnf install java-11-openjdk-devel

For JAVA 8:
------------
Enable the Oracle JDK 8 Repository:
Oracle JDK 8 is not available in the default repositories for Oracle Linux 8. You need to enable the Oracle JDK 8 repository. Here's how you can do it:

sudo dnf install -y oracle-epel-release-el8
sudo dnf config-manager --enable ol8_developer_Java

Install JDK 8:
---
sudo dnf install -y oracle-instantclient-release-el8
sudo dnf install -y oracle-instantclient18.5-basic oracle-instantclient18.5-sqlplus oracle-instantclient18.5-devel

Verify Installation:
---
After the installation is complete, you can verify it by checking the installed Java version:

java -version




Error:
-------------
Running transaction
RPM: error: db5 error(-30969) from dbenv->open: BDB0091 DB_VERSION_MISMATCH: Database environment version mismatch
RPM: error: cannot open Packages index using db5 -  (-30969)
RPM: error: cannot open Packages database in /var/lib/rpm
The downloaded packages were saved in cache until the next successful transaction.
You can remove cached packages by executing 'dnf clean packages'.
Error: Could not run transaction.

Clean RPM Database:
------
Run the following commands to clean the RPM database:

sudo rm -f /var/lib/rpm/__db*
sudo db_verify /var/lib/rpm/Packages

Rebuild RPM Database:
---
Rebuild the RPM database using the following commands:

sudo rpm --rebuilddb
sudo dnf clean all

Retry the Installation:
-----------
After rebuilding the RPM database, try installing the JDK again:


sudo dnf install -y oracle-instantclient-release-el8
sudo dnf install -y oracle-instantclient18.5-basic oracle-instantclient18.5-s


COnlfuent:

 https://packages.confluent.io/archive/6.2/confluent
 
 
 
Install unzip:
sudo yum install unzip


Set the environment variable for the Confluent Platform home directory.

export CONFLUENT_HOME=<The directory where Confluent is installed>
export CONFLUENT_HOME=~/confluent-7.5.3
Add the Confluent Platform bin directory to your PATH

export PATH=$PATH:$CONFLUENT_HOME/bin
Test that you set the CONFLUENT_HOME variable correctly by running the confluent command:

confluent --help

confluent local services start

Control center :
localhost:9021

https://docs.confluent.io/platform/current/installation/installing_cp/zip-tar.html
