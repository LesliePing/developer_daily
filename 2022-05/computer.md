# win10 关闭占用端口

```zsh
netstat -ano|findstr "7373"
taskkill  -F -PID 13192
```