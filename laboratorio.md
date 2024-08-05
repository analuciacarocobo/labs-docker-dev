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

