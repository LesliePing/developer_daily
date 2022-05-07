# 修改数据库密码
`update mysql.user set authentication_string=password('123') where user='root' and Host = 'localhost';`