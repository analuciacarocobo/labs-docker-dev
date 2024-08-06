# Este es el archivo del laboratorio

## 1.1 Descargar la imagen ofial de Ubuntu 
´´ bash 
$ docker pull ubuntu

Using default tag: latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

### 1.2 Descargar la Imagen de Python 3.9
´´ bash 
$ docker pull python:3.9

3.9: Pulling from library/python
ca4e5d672725: Pull complete 
30b93c12a9c9: Pull complete 
10d643a5fa82: Pull complete 
d6dc1019d793: Pull complete 
c7d45ab0573c: Pull complete 
564d1c451ea7: Pull complete 
ddfb50ba1977: Pull complete 
91b87d81d4c8: Pull complete 
Digest: sha256:65438c2e26dbf9f5db4b5553e332747fa20722c1b7c7ccc6f8480396ff4186db
Status: Downloaded newer image for python:3.9
docker.io/library/python:3.9

#### 2.1. Ejecutar un Contenedor de Ubuntu en Modo Interactivo
$ docker run -it ubuntu bash

root@ad940306d75a:/# 

##### 2.2 Ejecutar un Servidor Web Apache en Segundo Plano
 $ docker run -d -p 8000:80 httpd

 Unable to find image 'httpd:latest' locally
latest: Pulling from library/httpd
efc2b5ad9eec: Pull complete 
fce1785eb819: Pull complete 
4f4fb700ef54: Pull complete 
f214daa0692f: Pull complete 
05383fd8b2b3: Pull complete 
88ad12232aa1: Pull complete 
Digest: sha256:932ac36fabe1d2103ed3edbe66224ed2afe0041b317bcdb6f5d9be63594f0030
Status: Downloaded newer image for httpd:latest
3a0d3172277492f1110326ca0fae9ae504cea947462ed0262ca01b3f6821ac73

### 3.1. Eliminar el Contenedor de Ubuntu
 $ docker ps -a

 CONTAINER ID   IMAGE     COMMAND              CREATED         STATUS                     PORTS                                   NAMES
3a0d31722774   httpd     "httpd-foreground"   4 minutes ago   Up 4 minutes               0.0.0.0:8000->80/tcp, :::8000->80/tcp   festive_sinoussi
ad940306d75a   ubuntu    "bash"               9 minutes ago   Exited (0) 5 minutes ago                                           ecstatic_khorana

### 3.2. Eliminar Todos los Contenedores Detenidos
 $  docker container prune -f

 Deleted Containers:
ad940306d75aef6b7d32d9d08ffd4def68b73a9758530d824e8c18f653d62c33

Total reclaimed space: 5B



# output docker build 

@analuciacarocobo ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 24.3s (9/9) FINISHED                                                                               docker:default
 => [internal] load build definition from dockerfile                                                                      0.2s
 => => transferring dockerfile: 561B                                                                                      0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                          0.0s
 => [internal] load .dockerignore                                                                                         0.2s
 => => transferring context: 2B                                                                                           0.0s
 => [internal] load build context                                                                                         0.3s
 => => transferring context: 44.75kB                                                                                      0.0s
 => [1/4] FROM docker.io/library/ubuntu:latest                                                                            0.1s
 => [2/4] RUN apt-get update && apt-get install -y     curl     wget     vim     && apt-get clean                        21.2s
 => [3/4] WORKDIR /app                                                                                                    0.2s
 => [4/4] COPY . /app                                                                                                     0.3s
 => exporting to image                                                                                                    1.5s
 => => exporting layers                                                                                                   1.4s
 => => writing image sha256:efe32045e4c41825fa5abf154ec40da144a4e22edbc03c759aab56ee2ebef2d4                              0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     

 # construir

 @analuciacarocobo ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 13.6s (6/6) FINISHED                                                                               docker:default
 => [internal] load build definition from dockerfile                                                                      0.1s
 => => transferring dockerfile: 876B                                                                                      0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                          0.0s
 => [internal] load .dockerignore                                                                                         0.1s
 => => transferring context: 2B                                                                                           0.0s
 => CACHED [stage-1 1/2] FROM docker.io/library/ubuntu:latest                                                             0.0s
 => [stage-1 2/2] RUN apt-get update &&     apt-get install -y nginx &&     apt-get clean                                12.3s
 => exporting to image                                                                                                    0.8s
 => => exporting layers                                                                                                   0.6s
 => => writing image sha256:fce3cb79d3f33801657cacefe245f7742faa84a0328ee49b8f4e1746ae5f2e4e                              0.0s
 => => naming to docker.io/library/my-nginx:latest   

 # ejecutar  

 @analuciacarocobo ➜ /workspaces/labs-docker-dev (main) $ docker run -d -p 80:80 my-nginx:latest
ebabaef39a57d5595de62899302dbbb53e65c4fde79afccd214ff437ac86df99

# reconstruir

@analuciacarocobo ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 12.6s (6/6) FINISHED                                                                               docker:default
 => [internal] load build definition from dockerfile                                                                      0.1s
 => => transferring dockerfile: 989B                                                                                      0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                          0.0s
 => [internal] load .dockerignore                                                                                         0.1s
 => => transferring context: 2B                                                                                           0.0s
 => CACHED [stage-2 1/2] FROM docker.io/library/ubuntu:latest                                                             0.0s
 => [stage-2 2/2] RUN apt-get update && apt-get install -y nginx                                                         11.3s
 => exporting to image                                                                                                    0.8s
 => => exporting layers                                                                                                   0.6s
 => => writing image sha256:83616a966c51fcfffaa7f4dce70ed552554b906f1b07bc4cfffb77b6aa31a658                              0.0s
 => => naming to docker.io/library/my-nginx:latest       

 # workdir

@analuciacarocobo ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 0.6s (6/6) FINISHED                                                                                             docker:default
 => [internal] load build definition from dockerfile                                                                                   0.1s
 => => transferring dockerfile: 1.15kB                                                                                                 0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                       0.0s
 => [internal] load .dockerignore                                                                                                      0.1s
 => => transferring context: 2B                                                                                                        0.0s
 => [stage-2 1/2] FROM docker.io/library/ubuntu:latest                                                                                 0.0s
 => CACHED [stage-2 2/2] RUN apt-get update && apt-get install -y nginx                                                                0.0s
 => exporting to image                                                                                                                 0.1s
 => => exporting layers                                                                                                                0.0s
 => => writing image sha256:aa9d2eb6bbc732001ae1cc5ecbda5a0b5753afa99e0c0033d7839fea04d6a86e                                           0.0s
 => => naming to docker.io/library/my-nginx:latest          


 # script 

 @analuciacarocobo ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 3.8s (8/8) FINISHED                                                                                             docker:default
 => [internal] load build definition from dockerfile                                                                                   0.1s
 => => transferring dockerfile: 111B                                                                                                   0.0s
 => [internal] load metadata for docker.io/library/python:3.9                                                                          0.0s
 => [internal] load .dockerignore                                                                                                      0.1s
 => => transferring context: 2B                                                                                                        0.0s
 => CACHED [1/3] FROM docker.io/library/python:3.9                                                                                     0.0s
 => [internal] load build context                                                                                                      0.1s
 => => transferring context: 30B                                                                                                       0.0s
 => [2/3] WORKDIR /app                                                                                                                 0.3s
 => [3/3] COPY script.py .                                                                                                             0.3s
 => exporting to image                                                                                                                 2.7s
 => => exporting layers                                                                                                                2.6s
 => => writing image sha256:24166d6de27880e94c07fceaf698280e8bc4b48a036a5be68ec3e8b243b2a194                                           0.0s
 => => naming to docker.io/library/my-nginx:latest  