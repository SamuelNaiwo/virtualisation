# Deploying App

## Provision VM

1. Change directory into correct folder.

    ```
    cd virtualisation
    ```

2. Create a shell script file which will be used to automate certain tasks.

    ```
    touch provision.sh
    ```

3. Open the shell script file created and enter the following commands. `#!/bin/bash` is a shebang and it tells the shell what program to interpret the script with when executed. `sudo apt-get update -y` is used to fetch the latest version. `sudo apt-get upgrade -y` is used to download and install the latest version. `sudo apt-get install nginx -y` installs nginx for us.

```
#!/bin/bash

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
```

![Alt text](img/provision%20file%20for%20automation.png)

4. Open vagrant file and enter the following command.

    ```
    config.vm.provision "shell", path: "provision.sh"
    ```

    ![Alt text](img/sync%20app%20folder.png)

## Syncing App Folder

1. Open vagrant file.

2. To sync app folder to virtual machine use the command below.
   
    `config.vm.synced_folder "app", "/home/vagrant/app"`


3. Run the following command to start the vagrant environment. 

    `vagrant up`

4. Open your terminal/bash

5. Make sure you're in the right folder where your vagrant file and app folder is, then ssh in.

    `vagrant ssh`

6. Check to see that the app folder is in your virtual machine.

    `ls`

7. Change directory into your app folder in your virtual machine.

    `cd app`

## Testing Environment

1. Change directory into environment folder in virtualisation folder.
   
   ```
   cd environment
   ```

2. Check and make sure everything you need is in your environment folder.

    ```
    ls
    ```

3. Change directory into spec-tests folder.
   
   ```
   cd spec-tests
   ```

4. Install gem
   
   ```
   gem install bundler
   ```

   ![Alt text](img/gem%20install%20bundler.png)

5. Bundle up all the test

    ```
    bundle
    ```

6. Check against our virtual environment to see what is present and start all the test.
   
   ```
   rake spec
   ```

7. Check to see what tests have failed. Failed test are listed below.
   
   ```
   Nodejs
   Nodjs - version 6.x
   pm2
   ```

## Install NodeJS

1. Open terminal/bash window and now nstall Nodejs.

    ```
    sudo apt install nodejs -y
    ```

2. Upgrade python software.
    
    ```
    sudo apt install python-software-properties
    ```

3. Install Nodejs version that we need.

    ```
    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    ```

4. Run command to install the current version we just downloaded.
    
    ```
    sudo apt install nodejs -y
    ```

5. Check to see what version you have.
    
    ```
    nodejs --version
    ```

6. Run your test again in VS Code to see if Nodejs was installed correctly.

    ```
    rake spec
    ```

## Install PM2

1. Open terminal/bash windown and run the following command to install pm2. This is a package manager for Node.

    ```
    sudo npm install pm2 -g
    ```

2. Run your test again in VS Code to see if pm2 was installed correctly i

    ```
    rake spec
    ```

## Run The Application

1. Open terminal/bash window and cd into app folder.
   
   ```
   cd app
   ```

2. Check to see that everything is in your folder.

    ```
    ls
    ```

3. Run the following command to install.

    ```
    npm install
    ```

4. Run the app using one of the following commands

    ```
    nmp start
    node app.js
    ```