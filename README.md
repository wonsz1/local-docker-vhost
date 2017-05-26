# Simple vhost configuration for docker

### How to use

edit /etc/apache2/httpd.conf, uncoment proxy_module and proxy_http_module

edit /etc/apache2/extra/httpd-vhosts.conf and add paste

```
<VirtualHost *:80>
  ServerName localhost
  ProxyPass / http://localhost:8080/public/
</VirtualHost>
```

this will pass all request from addres http://localhost to addres with port 8080(which depends on your configuration in docker-compose.yml)

you should also have
```127.0.0.1 localhost```
in your /etc/hosts file

restart apache:
```sudo apachectl restart```

and check configuration:
```apachectl configtest```