# LAB8
Maxscale Replication
create user ‘maxscale’@’%’ identified by ‘11223344’;
grant replication slave on *.* to ‘maxscale’;
flush tables with read lock;
show master status;
unlock tables;
stop slave;
change master to 
master_host=’10.10.0.5’,
master_user=’maxscale’,
master_password=’11223344’,
master_log_file=’mariadb-bin.000003’,
master_log_pos=615;
start slave;
