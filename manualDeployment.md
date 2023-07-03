# Intro to manual deployment


## App

### Manually deploying an application
1. Installing node.js ```curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
  262  sudo apt install nodejs -y ```
2. Installing pm2 ``` sudo npm install pm2 -g ```
3. cd into an app folder
4. Use ``` npm install ```
5. Start the app by ```npm start``` OR ```node app.js```
6. Allow TCP access to port in Azure by adding a security rule: VM -> Networking -> Add inbount port rule
7. Change IP from local host

### Connecting the DB
1. Creating an env var by ```export DB_HOST=mongodb://51.142.192.154:27017/posts```

## DB
### Manually deploying a DB
1. Installing mongo DB  


```bash
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt update -y

sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
```
1. Configure mongo DB

From local host to allowing acces from everyone
```bash
sudo sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mongod.conf
```
2. Allow TCP access to port in Azure by adding a security rule: VM -> Networking -> Add inbount port rule