# Syncing App Folder

1. Open vagrant file.

2. To sync app folder to virtual machine use the command below.
   
    `config.vm.synced_folder "app", "/home/vagrant/app"`

    ![Alt text](img/sync%20app%20folder.png)

3. Run the following command to start the vagrant environment. 

    `vagrant up`

4. Open your terminal/bash

5. Make sure you're in the right folder where your vagrant file and app folder is, then ssh in.

    `vagrant ssh`

6. Check to see that the app folder is in your virtual machine.

    `ls`

7. Change directory into your app folder in your virtual machine.

    `cd app`

# Testing Environment

1. Change directory into environment folder in virtualisation folder.

2. ls to check

3. cd into spec-tests folder.

4. Install gem
   
   ```
   gem install bundler
   ```

   ![Alt text](img/gem%20install%20bundler.png)

5. Bundle up all the test

    ```
    bundle
    ```

6. Check against our virtual to see what is present and starts all the test.
   
   ```
   rake spec
   ```

7. Check to see what tests have failed. Failed test are listed below.
   
   ```
   Nodejs
   Nodjs - version 6.x
   pm2
   ```

8. Install Nodejs through your terminal/bash.

    ```
    sudo apt install nodejs -y
    ```

9. d
    
    ```
    sudo apt install python-software-properties
    ```

10. Install Nodejs version that we need.

    `curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`

11. Run same command to install the current version we just downloaded.
    
    ```
    sudo apt install nodejs -y
    ```

12. Check to see what version you have.
    
    ```
    nodejs --version
    ```

13. Run your test again to see if Nodejs was installed correctly.

    ```
    rake spec
    ```
