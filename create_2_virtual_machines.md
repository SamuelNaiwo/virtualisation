# Create 2 Virtual Machines

## Create First Virtual Machine
1. Open your vagrant file.

2. We had a virtual machine already created which was `config.vem.define "app" do |config|`. We renamed it to `config.vem.define "app" do |app|` to give it the name `app`

```
config.vem.define "app" do |app|
```

![Alt text](img/1.%20rename%20to%20app.png)

3. Add `end` at the end of the line to show when it is finished. Make sure it is in line with `config.vem.define "app" do |app|`
   
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

5. Use the command `vagrant up` to check that the new virtual machine is named `app`

```
vagrant up
```

## Create Second Virtual Machine
1. config.vm "db" do |db| on a new line to create a new virtual machine
2. Add these to lines and make sure they're indented - db.vm.box = "ubuntu/xenial64" db.vm.network "private_network", ip: "192.168.10.150" - last 3 digits can be between 0-255 but must be different to IP address above
3. add `end` at the end of the line to show when it is finished
4. comment out cd app in provision folder.
5. vagrant up to open both 

open first virtual box
4. Open terminal/bash window
5. cd into folder where vagrant file is
6. ls to check
7. vangrant ssh app
8. ls to check
9. nodejs --version check version
10. npm --version check version

open second virtual box
1. open new terminal/nbash window
2. cd into folder where vagrant file is
3. ls to check
4. vagrant ssh db
5. ls to check

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