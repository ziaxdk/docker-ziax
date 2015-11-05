# Build

<<<<<<< HEAD

sudo docker pull ziaxdk/node
sudo docker pull ziaxdk/nginx

sudo docker run -d --name node -p 8888:8888 ziaxdk/node
sudo docker run -d --name nginx -p 80:80 -p 443:443 --link node:node ziaxdk/nginx
=======
```
$ docker build -t ziaxdk/node .
$ docker build -t ziaxdk/nginx .
```

# Run

```
$ docker run -d --name node -p 8888:8888 node
$ docker run -d --name nginx -p 80:80 -p 443:443 --link node:node nginx
```
>>>>>>> 71d0fe4aef5ea445e83124b1dc5cf75d507f74fa
