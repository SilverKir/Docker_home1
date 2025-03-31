## Задание 1 - Docker CLI
### Загрузите образ busybox последней версии
### Запустите новый контейнер busybox с командой ping сайта netology.ru, и количеством пингов 7, поименуйте контейнер pinger

*C:\JS\Node\Docker_Home>docker run --name pinger -it busybox ping -c 7 netology.ru*
***
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
97e70d161e81: Pull complete
Digest: sha256:37f7b378a29ceb4c551b1b5582e27747b855bbfaa73fa11914fe0df028dc581f
Status: Downloaded newer image for busybox:latest
PING netology.ru (51.250.51.8): 56 data bytes
64 bytes from 51.250.51.8: seq=0 ttl=63 time=86.128 ms
64 bytes from 51.250.51.8: seq=1 ttl=63 time=81.802 ms
64 bytes from 51.250.51.8: seq=2 ttl=63 time=79.593 ms
64 bytes from 51.250.51.8: seq=3 ttl=63 time=79.351 ms
64 bytes from 51.250.51.8: seq=4 ttl=63 time=81.076 ms
64 bytes from 51.250.51.8: seq=5 ttl=63 time=80.043 ms
64 bytes from 51.250.51.8: seq=6 ttl=63 time=89.869 ms

--- netology.ru ping statistics ---
7 packets transmitted, 7 packets received, 0% packet loss
round-trip min/avg/max = 79.351/82.551/89.869 ms

### Выведите на список всех контейнеров - запущенных и остановленных
C:\JS\Node\Docker_Home>docker ps -a 
CONTAINER ID   IMAGE                             COMMAND                  CREATED         STATUS    
                   PORTS     NAMES
29f6486748cb   busybox                           "ping -c 7 netology.…"   2 minutes ago   Exited (0) 2 minutes ago               pinger
68216ffcb69b   mysql:latest                      "docker-entrypoint.s…"   4 weeks ago     Exited (0) 4 weeks ago                 users-db
2b91800dac9d   mysql                             "docker-entrypoint.s…"   5 weeks ago     Exited (0) 5 weeks ago                 SchoolDB
e9ac61253403   postgres                          "docker-entrypoint.s…"   4 months ago    Exited (0) 5 weeks ago                 mynewdb
696d035aacdb   redis:6.2.5                       "docker-entrypoint.s…"   12 months ago   Exited (0) 12 months ago               skillbox-redis
6df2d952c621   mongo:3.1                         "/entrypoint.sh mong…"   12 months ago   Exited (139) 12 months ago             skillbox-mongodb
67158e82c0a2   docker/welcome-to-docker:latest   "/docker-entrypoint.…"   12 months ago   Exited (0) 4 months ago                welcome-to-docker

### Выведите на экран логи контейнера с именем pinger
C:\JS\Node\Docker_Home>docker logs pinger
PING netology.ru (51.250.51.8): 56 data bytes
64 bytes from 51.250.51.8: seq=0 ttl=63 time=86.128 ms
64 bytes from 51.250.51.8: seq=1 ttl=63 time=81.802 ms
64 bytes from 51.250.51.8: seq=2 ttl=63 time=79.593 ms
64 bytes from 51.250.51.8: seq=3 ttl=63 time=79.351 ms
64 bytes from 51.250.51.8: seq=4 ttl=63 time=81.076 ms
64 bytes from 51.250.51.8: seq=5 ttl=63 time=80.043 ms
64 bytes from 51.250.51.8: seq=6 ttl=63 time=89.869 ms

--- netology.ru ping statistics ---
7 packets transmitted, 7 packets received, 0% packet loss
round-trip min/avg/max = 79.351/82.551/89.869 ms

### Запустите второй раз контейнера с именем pinger
C:\JS\Node\Docker_Home>docker start pinger                      
pinger

### Выведите на список всех контейнеров - запущенных и остановленных
C:\JS\Node\Docker_Home>docker ps -a       
CONTAINER ID   IMAGE                             COMMAND                  CREATED          STATUS   
                    PORTS     NAMES
29f6486748cb   busybox                           "ping -c 7 netology.…"   18 minutes ago   Exited (0) 31 seconds ago              pinger
68216ffcb69b   mysql:latest                      "docker-entrypoint.s…"   4 weeks ago      Exited (0) 4 weeks ago                 users-db
2b91800dac9d   mysql                             "docker-entrypoint.s…"   5 weeks ago      Exited (0) 5 weeks ago                 SchoolDB
e9ac61253403   postgres                          "docker-entrypoint.s…"   4 months ago     Exited (0) 5 weeks ago                 mynewdb
696d035aacdb   redis:6.2.5                       "docker-entrypoint.s…"   12 months ago    Exited (0) 12 months ago               skillbox-redis
6df2d952c621   mongo:3.1                         "/entrypoint.sh mong…"   12 months ago    Exited (139) 12 months ago             skillbox-mongodb
67158e82c0a2   docker/welcome-to-docker:latest   "/docker-entrypoint.…"   12 months ago    Exited (0) 4 months ago                welcome-to-docker

### Выведите на экран логи контейнера с именем pinger
C:\JS\Node\Docker_Home>docker logs -t pinger
2025-03-31T02:24:18.709948100Z PING netology.ru (51.250.51.8): 56 data bytes
2025-03-31T02:24:18.796574725Z 64 bytes from 51.250.51.8: seq=0 ttl=63 time=86.128 ms
2025-03-31T02:24:19.794434127Z 64 bytes from 51.250.51.8: seq=1 ttl=63 time=81.802 ms
2025-03-31T02:24:20.792684487Z 64 bytes from 51.250.51.8: seq=2 ttl=63 time=79.593 ms
2025-03-31T02:24:21.792735713Z 64 bytes from 51.250.51.8: seq=3 ttl=63 time=79.351 ms
2025-03-31T02:24:22.795417947Z 64 bytes from 51.250.51.8: seq=4 ttl=63 time=81.076 ms
2025-03-31T02:24:23.794096308Z 64 bytes from 51.250.51.8: seq=5 ttl=63 time=80.043 ms
2025-03-31T02:24:24.804582415Z 64 bytes from 51.250.51.8: seq=6 ttl=63 time=89.869 ms
2025-03-31T02:24:24.804630916Z
2025-03-31T02:24:24.804639953Z --- netology.ru ping statistics ---
2025-03-31T02:24:24.804647317Z 7 packets transmitted, 7 packets received, 0% packet loss
2025-03-31T02:24:24.804654240Z round-trip min/avg/max = 79.351/82.551/89.869 ms
2025-03-31T02:42:26.704818079Z PING netology.ru (51.250.51.8): 56 data bytes
2025-03-31T02:42:26.797861123Z 64 bytes from 51.250.51.8: seq=0 ttl=63 time=91.222 ms
2025-03-31T02:42:27.797234942Z 64 bytes from 51.250.51.8: seq=1 ttl=63 time=87.461 ms
2025-03-31T02:42:28.793416798Z 64 bytes from 51.250.51.8: seq=2 ttl=63 time=82.928 ms
2025-03-31T02:42:29.821267815Z 64 bytes from 51.250.51.8: seq=3 ttl=63 time=110.588 ms
2025-03-31T02:42:30.792037711Z 64 bytes from 51.250.51.8: seq=4 ttl=63 time=80.743 ms
2025-03-31T02:42:31.792373637Z 64 bytes from 51.250.51.8: seq=5 ttl=63 time=80.313 ms
2025-03-31T02:42:32.803502822Z 64 bytes from 51.250.51.8: seq=6 ttl=63 time=89.964 ms
2025-03-31T02:42:32.803584736Z
2025-03-31T02:42:32.803602469Z --- netology.ru ping statistics ---
2025-03-31T02:42:32.803613750Z 7 packets transmitted, 7 packets received, 0% packet loss
2025-03-31T02:42:32.803632335Z round-trip min/avg/max = 80.313/89.031/110.588 

## Определите по логам общее количество запусков команды ping и какое общее количество отправленых запросов
Общее количество запусков команды ping - 2 раза
Общее количество отправленых запросов - 14

### Удалите контейнер с именем pinger

C:\JS\Node\Docker_Home>docker rm pinger     
pinger

C:\JS\Node\Docker_Home>docker ps -a
CONTAINER ID   IMAGE                             COMMAND                  CREATED         STATUS    
                   PORTS     NAMES
68216ffcb69b   mysql:latest                      "docker-entrypoint.s…"   4 weeks ago     Exited (0) 4 weeks ago                 users-db
2b91800dac9d   mysql                             "docker-entrypoint.s…"   5 weeks ago     Exited (0) 5 weeks ago                 SchoolDB
e9ac61253403   postgres                          "docker-entrypoint.s…"   4 months ago    Exited (0) 5 weeks ago                 mynewdb
696d035aacdb   redis:6.2.5                       "docker-entrypoint.s…"   12 months ago   Exited (0) 12 months ago               skillbox-redis
6df2d952c621   mongo:3.1                         "/entrypoint.sh mong…"   12 months ago   Exited (139) 12 months ago             skillbox-mongodb
67158e82c0a2   docker/welcome-to-docker:latest   "/docker-entrypoint.…"   12 months ago   Exited (0) 4 months ago                welcome-to-docker

### Удалите образ busybox
C:\JS\Node\Docker_Home>docker images
REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE
postgres                   latest    80cbdc6c3301   4 months ago    435MB
mysql                      latest    10db11fef9ce   5 months ago    602MB
busybox                    latest    ff7a7936e930   6 months ago    4.28MB
docker/welcome-to-docker   latest    c1f619b6477e   16 months ago   18.6MB
redis                      6.2.5     5d89766432d0   3 years ago     105MB
mongo                      3.1       199e537da3a8   8 years ago     303MB

C:\JS\Node\Docker_Home>docker rmi busybox
Untagged: busybox:latest
Untagged: busybox@sha256:37f7b378a29ceb4c551b1b5582e27747b855bbfaa73fa11914fe0df028dc581f
Deleted: sha256:ff7a7936e9306ce4a789cf5523922da5e585dc1216e400efb3b6872a5137ee6b
Deleted: sha256:068f50152bbc6e10c9d223150c9fbd30d11bcfd7789c432152aa0a99703bd03a

C:\JS\Node\Docker_Home>docker images      
REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE
postgres                   latest    80cbdc6c3301   4 months ago    435MB
mysql                      latest    10db11fef9ce   5 months ago    602MB
docker/welcome-to-docker   latest    c1f619b6477e   16 months ago   18.6MB
redis                      6.2.5     5d89766432d0   3 years ago     105MB
mongo                      3.1       199e537da3a8   8 years ago     303MB
