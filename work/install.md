Install JAVA8 AND MYSQL5.7 ON RHEL7

sudo yum update 

sudo yum install java-1.8.0-openjdk-devel -y 

sudo update-alternatives --config java 

java -version 

----------------------------------------------------------------------------------------------

sudo yum install unzip wget -y 

wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm

sudo yum localinstall -y mysql57-community-release-el7-11.noarch.rpm

sudo yum repolist enabled | grep "mysql.*-community.*"

sudo yum install mysql-community-server

sudo service mysqld start/status

sudo grep 'temporary password' /var/log/mysqld.log

sudo mysql_secure_installation

mysql –u root -p

----------------

sudo yum remove mysql mysql-server
sudo mv /var/lib/mysql /var/lib/mysql_old_backup
sudo mv /etc/mysql /etc/mysql_old_backup

sudo yum module disable mysql

----------------------------------------------------------------------------------------------------------

Oracle JAVA8

Use the below link for jdk8 download.
https://www.oracle.com/in/java/technologies/javase/javase8-archive-downloads.html

yum install yum-utils && clean all

sudo yum provides ld-linux.so.2

sudo yum install libgcc_s.so.1

sudo yum localinstall jdk-8u251-linux-i586.rpm







