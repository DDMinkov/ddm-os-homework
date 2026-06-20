Варіант B:

Запуск контейнера:

ddminkov@ddminkov-virtual-machine:~$ docker run -d --name broken-nginx nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
c82e83b01f69: Pull complete 
72c03230f136: Pull complete 
8da80f8205ea: Pull complete 
ac5e3151b8c0: Pull complete 
3461bb328618: Pull complete 
99181f19640f: Pull complete 
868d78dceaed: Pull complete 
4b84eff91c61: Download complete 
bcac76e1b5c9: Download complete 
Digest: sha256:42f2d24ae18df9b5251d1cc45548085656d2335e9338fd150a24e415462d151f
Status: Downloaded newer image for nginx:latest
5e836dd2017225ebc21741e012e607eecc18f4d96ef2923e934791b4b73a6d6a

Перевірка port mapping:

ddminkov@ddminkov-virtual-machine:~$ docker ps --format "table {{.Names}}\t{{.Ports}}\t{{.Status}}"
NAMES          PORTS     STATUS
broken-nginx   80/tcp    Up 3 minutes

Результат ss / netstat усередині контейнера:

ddminkov@ddminkov-virtual-machine:~$ docker exec broken-nginx ss -tlnp
State  Recv-Q Send-Q Local Address:Port Peer Address:PortProcess
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1,fd=7))

Виправлення:

ddminkov@ddminkov-virtual-machine:~$ docker rm -f broken-nginx
broken-nginx
ddminkov@ddminkov-virtual-machine:~$ docker run -d --name fixed-nginx -p 8080:80 nginx
a43c0d3acbd6f829aef4564266f11c0daae1d60db0f9bafdd9e7d624d1be9b7e
ddminkov@ddminkov-virtual-machine:~$ docker ps --format "table {{.Names}}\t{{.Ports}}"
NAMES         PORTS
fixed-nginx   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp

Результат:

ddminkov@ddminkov-virtual-machine:~$ curl -I http://localhost:8080
HTTP/1.1 200 OK
Server: nginx/1.31.2
Date: Sat, 20 Jun 2026 16:10:55 GMT
Content-Type: text/html
Content-Length: 896
Last-Modified: Wed, 17 Jun 2026 14:40:35 GMT
Connection: keep-alive
ETag: "6a32b1e3-380"
Accept-Ranges: bytes
