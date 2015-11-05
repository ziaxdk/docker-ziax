docker build -t ziaxdk/node .
docker build -t ziaxdk/nginx .


sudo docker pull ziaxdk/node
sudo docker pull ziaxdk/nginx

sudo docker run -d --name node -p 8888:8888 ziaxdk/node
sudo docker run -d --name nginx -p 80:80 -p 443:443 --link node:node ziaxdk/nginx