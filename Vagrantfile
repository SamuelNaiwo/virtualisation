Vagrant.configure("2") do |config|
 
  config.vem.define "app" do |app|
    app.vm.box = "ubuntu/xenial64"
    app.vm.network "private_network", ip: "192.168.10.100"
    app.vm.sync-folder "app", "/home/vagrant/app"
    app.vm.provision "shell", path: "provision.sh"
  end
  
  config.vm "db" do |db|
    db.vm.box = "ubuntu/xenial64"
    db.vm.network "private_network", ip: "192.168.10.150"
  end  

end