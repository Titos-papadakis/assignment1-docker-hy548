HY-548 Assignment 1 - Docker 
Papadakis Ioannis -Titos CSD5200

1)

a)docker pull nginx:1.29.5-alpine && docker pull nginx:1.29.5
b)τρεχουμε το docker images ή το βλέπουμε από το docker desktop το σκετο 1.29.5 τρεχει σε Debian που είναι πληρης με πολλά εργαλεία ενώ το alpine είναι πιο minimal λειτουργικο και εχει τα βασικα οποτε είναι πιο ελαφρυ για αυτό υπαρχει διαφορα στα μεγεθη των εικονων 
c)
ετρεξα την εντολη docker run -d -p 8000:80 nginx:1.29.5 και μετα την curl localhost:8000

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

d) κανουμε docker ps για να δουμε ότι τρεχει και βγαζει αυτό :οποτε τρεχει κανονικα 
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                     NAMES
adfd5f064c78   nginx:1.29.5   "/docker-entrypoint.…"   8 minutes ago   Up 8 minutes   0.0.0.0:8000->80/tcp, [::]:8000->80/tcp   serene_vaughan

e)ετρεξα την εντολη docker logs adfd5f064c78 που αυτό ηταν το id του container και εβγαλε αυτό 
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/02/24 10:29:56 [notice] 1#1: using the "epoll" event method
2026/02/24 10:29:56 [notice] 1#1: nginx/1.29.5
2026/02/24 10:29:56 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19)
2026/02/24 10:29:56 [notice] 1#1: OS: Linux 6.6.87.2-microsoft-standard-WSL2
2026/02/24 10:29:56 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/02/24 10:29:56 [notice] 1#1: start worker processes
2026/02/24 10:29:56 [notice] 1#1: start worker process 29
2026/02/24 10:29:56 [notice] 1#1: start worker process 30
2026/02/24 10:29:56 [notice] 1#1: start worker process 31
2026/02/24 10:29:56 [notice] 1#1: start worker process 32
2026/02/24 10:29:56 [notice] 1#1: start worker process 33
2026/02/24 10:29:56 [notice] 1#1: start worker process 34
2026/02/24 10:29:56 [notice] 1#1: start worker process 35
2026/02/24 10:29:56 [notice] 1#1: start worker process 36
2026/02/24 10:29:56 [notice] 1#1: start worker process 37
2026/02/24 10:29:56 [notice] 1#1: start worker process 38
2026/02/24 10:29:56 [notice] 1#1: start worker process 39
2026/02/24 10:29:56 [notice] 1#1: start worker process 40
2026/02/24 10:29:56 [notice] 1#1: start worker process 41
2026/02/24 10:29:56 [notice] 1#1: start worker process 42
2026/02/24 10:29:56 [notice] 1#1: start worker process 43
2026/02/24 10:29:56 [notice] 1#1: start worker process 44
172.17.0.1 - - [24/Feb/2026:10:34:47 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/8.16.0" "-"

f)ετρεξα την εντολη docker stop adfd5f064c78 και μου εβγαλε αυτό από κατω (το id του container)
adfd5f064c78
g)ετρεξα την εντολη docker start adfd5f064c78 και μου εβγαλε αυτό από κατω (το id του container)
adfd5f064c78
h) ετρεξα την εντολη docker stop adfd5f064c78 και μου εβγαλε 
adfd5f064c78
ετρεξα και αυτη την εντολη docker rm -f adfd5f064c78 και μου εβγαλε 
adfd5f064c78
όταν βαζουμε την παραμετρο -f δε χρειαζεται να κανουμε stop και από πριν γιατι κανει και stop  και remove μαζι αρα και μονη της θα μπορουσε να παιξει χωρις το docker stop στην αρχη

2)

a)docker exec -it thirsty_zhukovsky sh && cd usr/share/nginx/html && cat index.html && echo "Welcome to MY nginx" && cat index.html
b)docker cp thirsty_zhukovsky:/usr/share/nginx/html/index.html C:\Users\titos\index.html && cp C:\Users\titos\index.html thirsty_zhukovsky:/usr/share/nginx/html/index.html && curl http://localhost:8000
c)όχι δεν βλεπω τις αλλαγες γιατι τις εκανα τοπικα στο συγκεκριμενο container και όταν το διαγραφεις ολες οι αλλαγες που κανεις χανονται , θα κρατιοντουσαν μονο αν εκανα αλλαγες με το volume και κρατουσα το ιδιο ακριβως container και να εκανα commit την εικονα
d)docker run -d -p 8000:80 -v C:/Users/titos/index/:/usr/share/nginx/html nginx && curl localhost:8000

3)

a)
b)
c)


4)
Yaml
