## Deploy to nginx


这里最点关注的是加上proxy_set_header X-Forwarded-For $remote_addr;这行配置，因为我们的django要获取真实的客户端IP的，加上这个之后，django就也可以获取到真实的客户端IP了。

```conf
server {
    charset utf-8;
    listen       80;
    server_name  alv.pub t.alv.pub sophiroth.com;

    rewrite ^(.*) https://$server_name$1 permanent;


}
server {
    charset utf-8;
    listen       443 ssl;
    server_name  alv.pub t.alv.pub sophiroth.com;

    proxy_set_header X-Forwarded-Proto https;
    ssl_certificate      conf.d/alv.pub.pem;
    ssl_certificate_key  conf.d/alv.pub.key;

    ssl_session_cache    shared:SSL:1m;
    ssl_session_timeout  5m;

    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers  on;
    proxy_set_header X-Forwarded-For $remote_addr;

    location / {
        proxy_pass http://172.17.0.1:8003/;
    }


```