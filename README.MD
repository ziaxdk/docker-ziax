# Utils

```
$ sudo mkdir d
$ sudo mount -t vboxsf d/Desktop d
```

## Run

```
$ sudo docker run -d --name es -p 9200:9200 -v /home/ziaxdk/es/:/usr/share/elasticsearch/data/ ziaxdk/es
$ sudo docker run -d --name node -p 8888:8888 --link es:es ziaxdk/node
$ sudo docker run -d --name nginx -p 80:80 -p 443:443 --link es:es --link node:node ziaxdk/nginx
```

## Build

```
$ docker build -t ziaxdk/node .
$ docker build -t ziaxdk/nginx .
$ docker build -t ziaxdk/es .
```
