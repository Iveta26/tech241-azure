## Intro to automation


### Launcing the app

```
sudo apt update -y

sudo apt upgrade -y

cd tech241-sparta-app

export DB_HOST=mongodb://51.142.192.154:27017/posts

npm install

pm2 start app.js # <- pm2 runds in the background

```


### Launching the DB

```
#!/bin/bash


sudo apt update -y

sudo apt upgrade -y

sudo sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mongod.conf

sudo systemctl start mongod

sudo systemctl enable mongod
```