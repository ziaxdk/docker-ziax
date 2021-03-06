## Build

```
$ docker build -t ziaxdk/es .
$ docker build -t ziaxdk/node .
$ docker build -t ziaxdk/nginx .
$ docker build -t ziaxdk/fluentd .
```

## Run

### with fluentd logs

```
$ sudo docker run -d --name es -p 9200:9200 -v /home/ziaxdk/es/:/usr/share/elasticsearch/data/ ziaxdk/es
$ sudo docker run -d --name node -e APP_PORT=3000 -p 3000:3000 --link es:es ziaxdk/node
$ sudo docker run -d --name fluentd -p 24224:24224 -p 24244:24244 --link es:es ziaxdk/fluentd
$ sudo docker run -d --name nginx -p 80:80 -p 443:443 --link es:es --link node:node --log-driver=fluentd --log-opt fluentd-tag=docker.nginx ziaxdk/nginx
$ sudo docker run -d --name kibana -p 5601:5601 --link es:elasticsearch kibana
```

### Commit to hub

```
$ docker login
$ docker push ziaxdk/es
$ docker push ziaxdk/node
$ docker push ziaxdk/nginx
$ docker push ziaxdk/fluentd
```

# Utils

### Boot2docker

```
$ sudo mkdir /d
$ sudo mount -t vboxsf d/Desktop /d
```

```
$ docker rm $(docker ps -a -q) # remove all
```

### Test logging

```
$ docker run --name logubuntu --rm --log-driver=fluentd --log-opt fluentd-tag=docker.logubuntu ubuntu echo "Rulez the nation!!"
$ docker run --rm --log-driver=fluentd --log-opt fluentd-tag=docker.logalpine alpine echo "Hello world!"

```
