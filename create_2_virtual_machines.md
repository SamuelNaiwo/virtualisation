# Create 2 Virtual Machines

## Create First Virtual Machine

1. Open your vagrant file.

2. We had a virtual machine already created which was `config.vem.define "app" do |config|`. We renamed it to `config.vem.define "app" do |app|` to give it the name `app`

    ```
    config.vem.define "app" do |app|
    ```

    ![Alt text](img/1.%20rename%20to%20app.png)

3. Add `end` at the end of the to show when it is finished. Make sure it is in line with `config.vem.define "app" do |app|`
   
    ```
    end
    ```

    ![Alt text](img/2.%20add%20end.png)

4. Change the names from `config` to `app` which is the new name of virtual machine we are creating.

    ```
    app.vm.box = "ubuntu/xenial64"
    app.vm.network "private_network", ip: "192.168.10.100"
    app.vm.sync-folder "app", "/home/vagrant/app"
    app.vm.provision "shell", path: "provision.sh"
    ```

    ![Alt text](img/3.%20change%20name%20to%20app%20from%20config.png) [label](create_2_virtual_machines.md)

5. Use the command `vagrant up app` to launch the machine.

```
vagrant up
```

## Create Second Virtual Machine

1. In the vagrant file again, type `config.vm "db" do |db|` on a new line to create a new virtual machine

    ```
    config.vm "db" do |db|
    ```

    ![Alt text](img/4.%20second%20virtual%20machine.png)

2. Add these to lines underneath and make sure they're indented. `db.vm.box = "ubuntu/xenial64"` `db.vm.network "private_network", ip: "192.168.10.150"`. Last 3 digits can be between 0-255 but must be different to IP address above in the first virtual machine.

    ```
    db.vm.box = "ubuntu/xenial64"
    db.vm.network "private_network", ip: "192.168.10.150"
    ```

    ![Alt text](img/5.%202%20commands%20added.png)

3. Comment out the last 3 lines in script to stop the app from launching.

    ![Alt text](img/6.%20comment%20out%20script.png)

4. Use the command `vagrant up db` to launch the second virtual machine.

    ```
    vagrant up db
    ```

## Open first virtual box

1. Open a terminal/bash window.

2. Change directory into the folder where your vagrant file is.

3. Use the command `ls` to check if the vagrant file is in the folder.

4. Use the command `vangrant ssh app` to ssh into into the virtual machine.

5. Use the command `ls` again to check.

6. Use the command `nodejs --version` to check what version of NodeJs you have. 

7. Use the command `npm --version` to check what version you have.

## Open second virtual box

1. Open a new terminal/bash window

2. Change directory into the folder where the vagrant file is.

3. Use the command `ls` to check if the vagrant file is in the folder.

4. Use the command `vangrant ssh db` to ssh into into the virtual machine.

5. Use the command `ls` again to check.

# Set Up MongoDB

1. Cd into db virtual machine
   
2. Run sudo apt update -y

    ```
    sudo apt update -y
    ```

3. run sudo apt upgrade -y

    ```
    sudo apt upgrade -y
    ```

4. Download

    ```
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927
    ```

5. Verify the key with the command below.

    ```
    echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
    ```

6. Run another update to grab the packages for MongoDB

    ```
    sudo apt update -y
    ```

7. Run another upgrade to download on our machine.

    ```
    sudo apt upgrade -y
    ```

8. Install MongoDB on your virtual machine
   
    ```
    sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
    ```

9. Start MongoDB

    ```
    sudo systemctl start mongod
    ```

10. Check to see it is running

    ```
    sudo systemctl status mongod
    ```