# Build

```
$ docker build -t ziaxdk/node .
$ docker build -t ziaxdk/nginx .
```

# Run

```
$ docker run -d --name node -p 8888:8888 node
$ docker run -d --name nginx -p 80:80 -p 443:443 --link node:node nginx
```
