Vagrant.configure("2") do |config|


   config.vm.define "manager" do |manager|
    manager.vm.box = "centos/7"
        manager.vm.network "private_network", ip: "192.168.33.150"
	manager.vm.hostname = "manager.dexter.com.br" 
       config.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        end

    manager.vm.provision "shell", inline: <<-SHELL
	echo "nameserver 192.168.33.153" > /etc/resolv.conf 
	SHELL


        end



   config.vm.define "worker1" do |worker1|
    worker1.vm.box = "ubuntu/xenial64"
        worker1.vm.network "private_network", ip: "192.168.33.151"
	worker1.vm.hostname = "worker1.dexter.com.br" 

       config.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        end

 
    worker1.vm.provision "shell", inline: <<-SHELL
	echo "nameserver 192.168.33.153" > /etc/resolv.conf 
	SHELL

  end


   config.vm.define "worker2" do |worker2|
    worker2.vm.box = "ubuntu/xenial64"
        worker2.vm.network "private_network", ip: "192.168.33.152"
	worker2.vm.hostname = "worker2.dexter.com.br" 

       config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        end

    worker2.vm.provision "shell", inline: <<-SHELL
	echo "nameserver 192.168.33.153" > /etc/resolv.conf 
	SHELL


end

   config.vm.define "ragnar" do |ragnar|
    ragnar.vm.box = "ubuntu/xenial64"
        ragnar.vm.network "private_network", ip: "192.168.33.153"
	ragnar.vm.hostname = "ragnar.dexter.com.br" 

       config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        end


    config.vm.provision "shell", inline: <<-SHELL
	apt-get update && apt-get install python -y 
	SHELL


	
	ragnar.vm.provision "ansible" do |ansibleragnar|
	ansibleragnar.playbook = "ragnar.yaml"
	end


end
   


end












