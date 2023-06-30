## Intro to automation

### Using sed

```sed``` is used to change contents in a file

This can be used to change bindIP in mongod.config
```sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf```


### npm start vs pm2 start
pm2 runs in the background, while npm does not. It will stop running with the script.

We can make npm run in the backround using **nohup** (no hang up) and &.

```bash
pkill -f npm #program kill force all npm
nohup npm start &
```

### Launcing the app

```bash
sudo apt update -y

sudo apt upgrade -y

# download node js for npm and pm2
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -


cd tech241-sparta-app

#this connects to the DB
export DB_HOST=mongodb://51.142.192.154:27017/posts

npm install

pm2 start app.js # <- pm2 runds in the background

```


### Launching the DB

```bash


#!/bin/bash

sudo apt update -y

sudo apt upgrade -y


wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt update -y

sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf

sudo systemctl start mongod

sudo systemctl enable mongod

```