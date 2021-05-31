<p>Файл конфига nginx по-умолчанию <a href="../nginx/files/nginx-default.conf">по ссылке</a> </p>
<p>1. Настройка WildFly + Nginx. В данном случае Nginx выступает в качестве обратного прокси:</p>
<pre><code>events {
  worker_connections  4096;  ## Default: 1024
}
http {
 server {
   listen 80;
   listen [::]:80;

   server_name medomain.com;

   location / {
       proxy_pass http://medomain:8080/;
       proxy_set_header Host $host;
   }
 }
 server {
   listen 90;
   listen [::]:90;

   server_name medomain.com;

   location / {
       proxy_pass http://medomain:9990/;
       proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
       proxy_set_header Host $server_addr:$server_port;
       proxy_set_header X-Real-IP $remote_addr;
   }
 }
}</code></pre>
<p>2. Настройка Nginx в качестве балансировщика.</p>
<p>2.1. По-умолчаню:</p>
<pre><code>http {
  # ...
  upstream backend {
    server app1.domain.com:8080;
    server app2.domain.com:8081;
  }
  server {
    listen 80;
    server_name medomain.com;

  location / {
    proxy_pass http://backend;
    }
  }
}</code></pre>
<p>3. Отображение статичного контенкта:</p>
<pre><code>http {
  # ...
  server {
    listen 80;
    server_name medomain.com;
  location / {
      root /var/www/medomain;
    }

  location ~ \.(woff|woff2)$ {
      root /var/www/medomain/fonts;
    }
  location ~ \.(gif|jpg|png)$ {
      root /var/www/medomain/images;
    }
  }
}</code></pre>