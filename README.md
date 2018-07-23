# docker 该项目为addcn/docker-lnmp 地址是：https://github.com/addcn/docker-lnmp.git
# 本人只是为了方便使用保存在自己的GitHub 侵权立删

#构建镜像：

  docker build --tag addcn/mysql -f mysql/Dockerfile .  <br>
  docker build --tag addcn/php7 -f php7/Dockerfile .  <br>
  docker build --tag addcn/nginx -f nginx/Dockerfile .  <br>

#启动容器：

  docker run --name mysql -p 3306:3306 -v /root/bo/data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -it addcn/mysql  <br>
  docker run --name php7 -p 9000:9000 -v /var/www/html:/usr/local/nginx/html --link mysql:mysql -it addcn/php7  <br>
  docker run --name nginx -p 80:80 -v /var/www/html:/usr/local/nginx/html --link php7:php7 -it addcn/nginx  <br>

