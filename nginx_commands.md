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

a)docker build -t titos/example:latest . docker images , η δική μου είναι μεγαλύτερη γιατί πρόσθεσα layers από πάνω
django,vim κλπ
b)Μετά την προσθήκη φακέλου και το rebuild τα κοντεινερς τρέχουν κανονικά και για να δω ότι υπάρχει διαφορά μπήκα στο 8000 και στο 8001 με ενα non existing page και στο ενα εβγαλε απλα ενα μηνυμα λαθους ενω στο αλλο ηταν αναλυτικο και το πανω μερος ηταν και κιτρινο 
docker build -t titos/django-app:latest . && docker run -d -p 8000:8000 --name django-debug titos/django-app:latest
&& docker run -d -p 8001:8000 -e DJANGO_DEBUG=0 --name django-nodebug titos/django-app:latest
&& docker ps &&  docker logs django-debug && docker logs django-nodebug && http://localhost:8000  
&& http://localhost:8001 && http://localhost:8000/some-non-existent-page && http://localhost:8001/some-non-existent-page

τα λογκς βγαλανε αυτο 

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
March 02, 2026 - 21:15:42
Django version 5.1.6, using settings 'mysite.settings'
Starting development server at http://0.0.0.0:8000/
Quit the server with CONTROL-C.


C:\Users\titos\Downloads\Pass_1234_Setup (1)\OneDrive\Υπολογιστής\548-ass1\assignment1-docker-hy548\django>



c) docker push titoyannis/django-app:latest 

και εβγαλε αυτο 

The push refers to repository [docker.io/titoyannis/django-app]
23b7d26ef1d2: Pushed
c7672f4959ea: Pushed
8566b36070c1: Pushed
07d1b5af933d: Pushed
b0b06581a769: Pushed
b617a119f8a2: Pushed
ed4a05daa2ca: Pushed
cee1f735bb4d: Pushed
beaa49fa38f1: Pushed
4f4fb700ef54: Pushed
1eb98adba0eb: Pushed
b871035c026b: Pushed
latest: digest: sha256:abe94c4aacf7e8989118a51a497f22400b2bfaa00c11299dada91d3170e5d237 size: 856




4) YAML

έκανα το github action στο .yml που κανει build και push αυτοματα το image στο Dockerhub με workflow dispatch 
τρεχει σε περιπου ενα λεπτο και το image υπάρχει στο https://hub.docker.com/r/titoyannis/django-app