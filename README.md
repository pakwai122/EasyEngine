# EasyEngine on Ubuntu wiht Wordpress,nginx,php7,mariadb,redis
```
####update and upgrade packages
sudo apt-get update && sudo apt-get -y dist-upgrade && sudo apt-get -y autoremove

####set timezone
sudo dpkg-reconfigure tzdata

####install easyengine
wget -qO ee rt.cx/ee && sudo bash ee

####set easyengine autocomplete 
source /etc/bash_completion.d/ee_auto.rc

#### install Nginx,Redis,Mysql, php7
sudo ee stack install --nginx --redis --mysql --php7
sudo ee site create yourdomain.com --wp --php7 --wpredis

#### check version of you site
ee site info yourdomain.com

#### secure header 
sudo vi /etc/nginx/nginx.conf
  add_header X-Content-Type-Options "nosniff" always;
  add_header X-Frame-Options SAMEORIGIN;
  add_header X-Xss-Protection "1; mode=block" always;
  more_clear_headers Server;

#### reload nginx
sudo nginx -t && sudo nginx -s reload

```
