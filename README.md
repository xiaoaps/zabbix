# zabbix
docker-compose zabbix

在启动zabbix.yml之前,先配置MySQL数据库目录挂载文件my.cnf
cat /docker/mysql/conf/my.cnf
[mysqld]
character-set-server=utf8
default_authentication_plugin=mysql_native_password
[client]
default-character-set=utf8
[mysql]
default-character-set=utf8

说明：
     如果是mysql服务器版本大于8.0.4，默认使用caching_sha2_password授权插件，而不是5.6/5.7使用的mysql_native_password进行身份验证。
     因此需要更改root账户的远程登录验证插件为mysql_native_password。
另外：
     通过docker内置zabbix-agent服务监控zabbix-server自身，需要设置Agent interfaces 
     IP address: 127.0.0.1,DNS name: zabbix-agent, Connect to: DNS
