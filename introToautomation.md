## Intro to automation

### Using sed

```sed``` is used to change contents in a file

This can be used to change bindIP in mongod.config
```sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf```


### npm start vs pm2 start
pm2 runs in the background, while npm does not. It will stop running with the script.

We can make npm run in the backround using **nohup** (no hang up) and **&**. **nohup* is telling the command not to "hang up" after the script is done running. **pkill** command is needed with this script to kill all the processes of npm first before we run it again. It is easier to use **pm2**.

```bash
pkill -f npm #program kill force all npm
nohup npm start &
```

### Launcing the app


Creating environmental var 

``` export DB_HOST=mongodb://172.166.128.199:27017/posts ``` 

This connects to the DB.

```bash

#!/bin/bash

# update <- to ensure package source list is up to date
sudo apt update -y


# upgrade <- installs latests packages of linux
sudo apt upgrade -y


# install nginx
sudo apt install nginx -y

# enable nginx - when VM restarts nginx will automatically start
sudo systemctl enable nginx

# install sed
sudo apt install sed -y

# setup reverse proxy
sudo sed -i 's#try_files $uri $uri/ =404;#proxy_pass http://localhost:3000;#g' /etc/nginx/sites-available/default

# restart to apply changes
sudo systemctl restart nginx

cat /etc/nginx/sites-available/default

# download node source
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

# install node js
sudo apt install nodejs -y

# install pm2
sudo npm install pm2 -g

# create env var. Enter IP and port of the DB
export DB_HOST=mongodb://172.166.128.199:27017/posts

git clone https://github.com/Iveta26/spartaApp sparta_app

cd sparta_app

# downloads required dependencies for nodejs. checks for DB_HOST var
npm install

#pm2 runs app in the background
pm2 start app.js


```

### Launching the DB

```bash

# runs a sub shell of bash to run a scrip (open bash shell to run the script)
#!/bin/bash

sudo apt update -y

sudo apt upgrade -y


# INSTALLING MONGODB

# downloading key for the right version
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt update -y

sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20


# changing bindIp form local to IP acessed by anyone
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf

# Start Mongo DB
sudo systemctl start mongod

# Enable Mongo DB. Runs on reboot
sudo systemctl enable mongod

```