# 修改数据库密码
`mysql > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'very_strong_password';
mysql > FLUSH PRIVILEGES;`

# ubuntu 安装 mysql
https://www.cnblogs.com/2020javamianshibaodian/p/12920243.html

# 允许远程访问
create user 'xxx'@'%' identified with mysql_native_password by 'password';
flush privileges;