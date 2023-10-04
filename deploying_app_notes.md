### App and Deployment with MongoDB server

1. Create Instance on AWS
2. Connect instance to Gitbash terminal. NOTE: May say "root" instead of "ubuntu". Change this
3. Setup Database Instance (a second instance). 
   4. NOTE: The security rules should have port range 22 and 27017
5. Connect the database instance to terminal.
   4. `sudo apt update`
   5. `sudo apt upgrade -y`
   6. `wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -`
      7. OK message
   8. `echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`
   9. `sudo apt update`
   10. `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20`
   11. `sudo nano /etc/mongod.conf`
       12. change the IP address to 0.0.0.0
   13. `sudo systemctl start mongod`
   14. `sudo systemctl enable mongod`
   15. `sudo systemctl status mongod`
       16. Should give green button and say 'active'
17. Add IP address to database instance `export DB_HOST=mongodb://<your_id_here>:27017/posts`
18. Go into the app with sparta app downloaded. 
19. Run commands:
    20. `npm install`
    21. `pm2 start app.js` OR `node app.js`
22. Copy and Paste public IP address into url:
    23. JUST URL - message should say Welcome to NginX
    24. <URL>:3000 - Message should say Welcome to the Sparta App
    25. <URL>:3000/posts - Message should say Sparta global's posts

```
#!/bin/bash

# update
sudo apt update -y

#upgrade
sudo apt upgrade -y

#install
sudo apt install nginx -y

#restart
sudo sysemctl restart nginx

#enable
sudo systemctl enable nginx

#install tree
sudo apt install tree

#install git
sudo apt install git-all

#install correct Nodejs version
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

#install NodeJs
sudo apt install nodejs -y

#install pm2
sudo npm install pm2 -g

#Create file to store app
mkdir nodejs_app


#Move into correct folder
cd nodejs_app

#clone from repo
git clone https://github.com/JK-A2023/Sparta_app.git
 

#Move into correct folder
cd Sparta_app/app


#Install dependencies
npm install -y

#Run file
pm2 start app.js
```