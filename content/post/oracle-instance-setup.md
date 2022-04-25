---
title: "Oracle Instance Setup"
date: 2021-12-19T07:05:02+05:30
draft: true
---


sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --add-service=https --permanent
sudo firewall-cmd --reload


sudo firewall-cmd --add-port=5000/tcp --permanent
sudo firewall-cmd --reload

sudo firewall-cmd --add-port=3306/tcp --permanent
sudo firewall-cmd --reload


# Set HTTPD File Permission
sudo /usr/sbin/setsebool -P httpd_can_network_connect 1
sudo  chcon -R -h -t httpd_sys_content_t /var/www/html
 
 
 # SQLPLUS 
 https://blogs.oracle.com/linux/post/connect-from-an-arm-based-a1-compute-shape-to-autonomous-database-two-ways
 
 
/home/opc/sqlcl/bin/sql /nolog
set cloudconfig /home/opc/Wallet_DB202112171711.zip
connect GROCERNEST@db202112171711_high
ad213&^%#AXHIUATE13



ocid1.vcn.oc1.ap-mumbai-1.amaaaaaazbp4xpqajo6mdiacijfeyiwnztdv274aszj3fwzlldsir54uuvha
ocid1.vcn.oc1.ap-mumbai-1.amaaaaaazbp4xpqajo6mdiacijfeyiwnztdv274aszj3fwzlldsir54uuvha

sqlcl/bin/sql /nolog
set cloudconfig /home/opc/oracle/wallets/testdb/Wallet_testdb.zip
Operation is successfully completed.
Operation is successfully completed.
Using temp directory:/tmp/oracle_cloud_config3986877764276892824
SQL> connect admin@testdb_high





PROD:
DB:::
Admin
asd821@!$&TQRB



Wallet : asd07213&%^@(GTJ


-Dspring.datasource.url="jdbc:oracle:thin:@db202203091858_medium?TNS_ADMIN=/home/opc/Wallet_DB202203091858" -Dspring.datasource.username="GROCERNEST" -Dspring.datasource.password="adjh1254#DRB"


PROD
GROCERNEST :: adjh1254#DRB
