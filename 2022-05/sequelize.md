# 基础

## 读写分离配置

```javascript
 const sequelize = new Sequelize('database', 'user', 'passwd', {
     dialect: 'mysql',
     port: 3306,
     replication: {
         read: [
             {host: '192.193.223.2', username: 'root',password: 'wewe'}
             {host: 'localhost', username: 'root',password: 'wwewe'}
         ],
         write: {host: 'localhost',username: 'root', password: 'wefew'}
     },
    pool: {
        maxConnections: 20,
        maxIdleTime: 30000
    }
 })
```