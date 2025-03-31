## Задание 2 - Environment Variables
 ### Загрузите образ node версии 15.14

 C:\JS\Node\Docker_Home>docker pull node:15.14
15.14: Pulling from library/node
bfde2ec33fbc: Pull complete
787f5e2f1047: Pull complete
7b6173a10eb8: Pull complete
dc05be471d51: Pull complete
55fab5cadd3c: Pull complete
bd821d20ef8c: Pull complete
6041b69671c6: Pull complete
989c5d2d2313: Pull complete
4b57d41e8391: Pull complete
Digest: sha256:608bba799613b1ebf754034ae008849ba51e88b23271412427b76d60ae0d0627
Status: Downloaded newer image for node:15.14
docker.io/library/node:15.14

What's Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview node:15.14


  C:\JS\Node\Docker_Home>docker images
REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE
postgres                   latest    80cbdc6c3301   4 months ago    435MB
mysql                      latest    10db11fef9ce   5 months ago    602MB
docker/welcome-to-docker   latest    c1f619b6477e   16 months ago   18.6MB
redis                      6.2.5     5d89766432d0   3 years ago     105MB
node                       15.14     3d3f41722daf   3 years ago     936MB
mongo                      3.1       199e537da3a8   8 years ago     303MB

### Запустите контейнер node в интерактивном режиме подключения терминала, поименуйте его mynode, передайте две переменные среды NAME=<ваше имя> и SURNAME=<ваша фамилия>

C:\JS\Node\Docker_Home>docker run --name mynode -e NAME=Kirill -e SURNAME=Serebrennikov -it node:15.14
Welcome to Node.js v15.14.0.
Type ".help" for more information.

### В интерактивной среде выполнения node выполните скрипт, который выведет на экран приветсвтие: Привет, <ваше имя> <ваша фамилия>!, эти данные должны быть получены из переменных среды

> console.log("Привет "+ process.env.NAME + " "+ process.env.SURNAME + "!")
Привет Kirill Serebrennikov!
undefined
>
### Остановите контейнер
(To exit, press Ctrl+C again or Ctrl+D or type .exit)
>
C:\JS\Node\Docker_Home>docker rm mynode
mynode