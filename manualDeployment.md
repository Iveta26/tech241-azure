# Into to manual deployment


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
2. Configure mongo DB
3. Allow TCP access to port in Azure by adding a security rule: VM -> Networking -> Add inbount port rule