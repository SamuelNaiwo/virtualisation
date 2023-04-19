# Create 2 Virtual Machines

## Create First Virtual Machine
1. Open your vagrant file.

2. This command below creates a new virtual machine and we are renaming it to `app`.

```
config.vem.define "app" do |app|
```

3. Add `end` at the end of the line to show when it is finished.
   
```
end
```   
4. Change the names from `config` to `app` which is the new name of virtual machine we are creating.


5. Vagrant up to check that the new virtual machine is named `app`

create second box
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