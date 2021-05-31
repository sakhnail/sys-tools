<p>Файл конфига nginx по-умолчанию <a href="../nginx/files/nginx-default.conf">по ссылке</a> </p>
<p>1. Настройка WildFly + Nginx. В данном случае Nginx выступает в качестве обратного прокси:</p>
<pre><code>events {
  worker_connections  4096;  ## Default: 1024
}
http {
 server {
   listen 80;
   listen [::]:80;

   server_name 192.168.40.82;

   location / {
       proxy_pass http://127.0.0.1:8080/;
       proxy_set_header Host $host;
   }
 }
 server {
   listen 90;
   listen [::]:90;

   server_name 192.168.40.82;

   location / {
       proxy_pass http://127.0.0.1:9990/;
       proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
       proxy_set_header Host $server_addr:$server_port;
       proxy_set_header X-Real-IP $remote_addr;
   }
 }
}</code></pre>
<p>2. Настройка Nginx в качестве балансировщика.</p>
<p>2.1. По-умолчаню:</p>
<pre><code>upstream test {
    	server localhost:8080;
    	server localhost:8081;
    }
    server {
    	listen 81;
    	server_name localhost;
    	client_max_body_size 1024M;
    	location / {
    		proxy_pass http://test;
    		proxy_set_header Host $host:$server_port;
    	}
    }</code></pre>