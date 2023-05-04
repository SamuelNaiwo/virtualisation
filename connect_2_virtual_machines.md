# How To Connect Two Virtual Machines

Making changes and merging from dev to main 12345678910

1. Open two seperate terminal/bash windows.

2. Change directory into virtualisation folder in both terminals.

3. Use the command below in your app virtual machine terminal to ssh into it.

```
vagrant ssh app
```

4. Use the command below in your db virtual machine terminal to ssh into it.

```
vagrant ssh db
```

5. Use `ls` to check app folder is in your app virtual machine.

```
ls
```

6. You can use `nodejs --version` or `node --version` depending on what what version of NodeJs you're using to check it is installed and what version is currently running

```
nodejs --version
node --version
```

7. Use the command `node pm2 --version` to check pm2 it is installed and what version is currently running.

```
node pm2 --version
```

8. In the db virtual machine use the command below to check MongoDB is active and running.

```
sudo systemctl status mongod
```

9. In db virtual machine use the command below to open the configuration file.

```
sudo nano /etc/mongod.conf
```

10. Go down to `# Network interfaces` and change `bindIp` to `0.0.0.0`

11. Save your changes and exit

12. Use the command below to restart mongodb after making changes.

```
sudo systemctl restart mongod
```

13. We then want to enable MongoDB to make sure the changes have taken place.

```
sudo systemctl enable mongod
```

14. Now check to make sure MongoDB is active and running.

```
sudo systemctl status mongod
```

15. In the app virtual machine terminal open your `.bashrc` folder. We are doing this so we can save our environment variables and make them persistent.

```
sudo nano .bashrc
```

16. Scroll down to the bottow and enter variables to tell the machine where we are connecting to. `export DB_HOST` is the variable name. `mongodb:` is where we are getting the data from. `//192.168.10.150` is the port and `27017:` is the server on MongoDB. `/posts` is the page created to pull data.

```
export DB_HOST=mongodb://192.168.10.150:27017/posts
```

17. We now have to update the changes we made with the below command.

```
source .bashrc
```

18. Check to see if the environment variable we just saved is there.

```
printenv DB_HOST
```

19. Change directory into app folder.

20. Check to see the file is in the app folder.

```
ls
```

21. Install the package with the below command.

```
npm install
```

22. Now seed the file into the mongo database with the below command.

```
seeds/seed.js
```

23. We can now run and start the app.

```
node app.js
```
