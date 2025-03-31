## Задание 3 - Volumes

### Загрузите образ node версии 15.14
### Запустите контейнер с именем first_node из образа node версии 15.14 в фоновом режиме, подключив папку data из текущей директории в /var/first/data контейнера

*C:\JS\Node\Docker_Home>docker run --name first_node -it -d -v C:\JS\Node\Docker_Home\data:/var/first/data node:15.14*
***
3e8e31a3c9df36496edbfbaecb350c12021b52a315aa7519d9fcc3be4d7706c1

### Запустите контейнер с именем second_node из образа node версии 15.14 в фоновом режиме, подключив папку data из текущей директории в /var/second/data контейнера
*C:\JS\Node\Docker_Home>docker run --name second_node -it -d -v %cd%\data:/var/second/data node:15.14*
***
961183fbf4b2dfc7ef1ce4625c36d0440c6fc8de3b80782b89515213f16fa531

### Подключитесь к контейнеру first_node с помощью exec и создайте текстовый файл любого содержания в /var/first/data

*C:\JS\Node\Docker_Home>docker exec first_node touch /var/first/data/test.txt*

### Добавьте еще один файл в папку data на хостовой машине

*C:\JS\Node\Docker_Home>echo "hello" > %cd%/data/file.txt*

### Подключитесь к контейнеру second_node с помощью exec и получите список файлов в директории /var/second/data, выведете на экран содержимое файлов

*C:\JS\Node\Docker_Home>docker exec second_node ls /var/second/data*
***
file.txt
test.txt

*C:\JS\Node\Docker_Home>docker exec second_node cat /var/second/data/file.txt*
***
"hello" 

*C:\JS\Node\Docker_Home>docker exec second_node cat /var/second/data/test.txt*

### Остановите оба контейнера
*C:\JS\Node\Docker_Home>docker stop first_node second_node*
***
first_node
second_node

*C:\JS\Node\Docker_Home>docker ps*
***
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

#### Удалите оба контейнера

*C:\JS\Node\Docker_Home>docker ps -a*
***
CONTAINER ID   IMAGE                             COMMAND                  CREATED         STATUS    
                        PORTS     NAMES
961183fbf4b2   node:15.14                        "docker-entrypoint.s…"   4 hours ago     Exited (137) About a minute ago             second_node
3e8e31a3c9df   node:15.14                        "docker-entrypoint.s…"   4 hours ago     Exited (137) About a minute ago             first_node
68216ffcb69b   mysql:latest                      "docker-entrypoint.s…"   4 weeks ago     Exited (0) 4 weeks ago                      users-db
2b91800dac9d   mysql                             "docker-entrypoint.s…"   5 weeks ago     Exited (0) 5 weeks ago                      SchoolDB
e9ac61253403   postgres                          "docker-entrypoint.s…"   4 months ago    Exited (0) 5 weeks ago                      mynewdb
696d035aacdb   redis:6.2.5                       "docker-entrypoint.s…"   12 months ago   Exited (0) 12 months ago                    skillbox-redis
6df2d952c621   mongo:3.1                         "/entrypoint.sh mong…"   12 months ago   Exited (139) 12 months ago                  skillbox-mongodb
67158e82c0a2   docker/welcome-to-docker:latest   "/docker-entrypoint.…"   12 months ago   Exited (0) 4 months ago                     welcome-to-docker

*C:\JS\Node\Docker_Home>docker rm first_node second_node*
***
first_node
second_node

*C:\JS\Node\Docker_Home>docker ps -a*
***
CONTAINER ID   IMAGE                             COMMAND                  CREATED         STATUS    
                   PORTS     NAMES
68216ffcb69b   mysql:latest                      "docker-entrypoint.s…"   4 weeks ago     Exited (0) 4 weeks ago                 users-db
2b91800dac9d   mysql                             "docker-entrypoint.s…"   5 weeks ago     Exited (0) 5 weeks ago                 SchoolDB
e9ac61253403   postgres                          "docker-entrypoint.s…"   4 months ago    Exited (0) 5 weeks ago                 mynewdb
696d035aacdb   redis:6.2.5                       "docker-entrypoint.s…"   12 months ago   Exited (0) 12 months ago               skillbox-redis
6df2d952c621   mongo:3.1                         "/entrypoint.sh mong…"   12 months ago   Exited (139) 12 months ago             skillbox-mongodb
67158e82c0a2   docker/welcome-to-docker:latest   "/docker-entrypoint.…"   12 months ago   Exited (0) 4 months ago                welcome-to-docker

### Удалите образ node версии 15.14

*C:\JS\Node\Docker_Home>docker images*
***
REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE
postgres                   latest    80cbdc6c3301   4 months ago    435MB
mysql                      latest    10db11fef9ce   5 months ago    602MB
docker/welcome-to-docker   latest    c1f619b6477e   16 months ago   18.6MB
redis                      6.2.5     5d89766432d0   3 years ago     105MB
node                       15.14     3d3f41722daf   3 years ago     936MB
mongo                      3.1       199e537da3a8   8 years ago     303MB

*C:\JS\Node\Docker_Home>docker rmi node:15.14*
***
Untagged: node:15.14
Untagged: node@sha256:608bba799613b1ebf754034ae008849ba51e88b23271412427b76d60ae0d0627
Deleted: sha256:3d3f41722daf1a77c34d6eade6676bbffa2d6a2a21095de2ab0c427a5c942fc9
Deleted: sha256:601382991a159cfc5013ad973158f30b7b7a913e8d7e547b3456deab3ad98022
Deleted: sha256:d5db49eecae8c02c9ea3a79f89c43ded9162bac118a0302a7b514d0df82aa112
Deleted: sha256:a2c1973858d0aad3de0927294602b17c8ef9050c30e0f461e0868997a08552a4
Deleted: sha256:a0153172017a08a521a8be971ca4dcb5fbc4b7227642c12bbb2da6265bd66b50
Deleted: sha256:f1123940e954d335d91b52a40fab4f8144f38ff113ade7d65663071d0f06da6f
Deleted: sha256:f1f4fbb0e7e6e0ce2d9eae1e577f9f6df0a719dd874bff00b2d08895c75c297d
Deleted: sha256:1eb455ab6d45fdbbd90fccff791ffa228080c052acf464f8da1b1d78650bd706
Deleted: sha256:1dbe832a694971a925d7d216f49b700c95f402bd72288f9d37eceb1d59dcf72d
Deleted: sha256:2f4ee6a2e1b5dfb9236cd262e788f9d39109242ca27a4aacb583c8af66ec3ff7


*C:\JS\Node\Docker_Home>docker images*
***         
REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE
postgres                   latest    80cbdc6c3301   4 months ago    435MB
mysql                      latest    10db11fef9ce   5 months ago    602MB
docker/welcome-to-docker   latest    c1f619b6477e   16 months ago   18.6MB
redis                      6.2.5     5d89766432d0   3 years ago     105MB
mongo                      3.1       199e537da3a8   8 years ago     303MB
