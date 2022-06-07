server {
      listen 7373  ssl;
      server_name www.xxx.top;

      ssl_certificate      www.xxx.pem;
      ssl_certificate_key  www.xxx.key;

      ssl_session_cache   shared:SSL:1m;
      ssl_session_timeout 5m;
       ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers  on;
      location / {
        root html/dist;
        index index.html index.htm;
        proxy_pass http://127.0.0.1:2346;
	# wss 配置要点
	proxy_http_version 1.1;
	proxy_set_header Upgrade $http_upgrade;
	proxy_set_header Connection "upgrade";
      }
    }

server {
        listen       443 ssl;
        server_name  www.xxx;

        ssl_certificate      www.xxx.pem;
        ssl_certificate_key  www.xxx.key;

        ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;

        ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers  on;

        location / {
            root   html;
            index  index.html index.htm;
	 }
    }