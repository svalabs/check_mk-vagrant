# CheckMk Vagrant 
#
#
PUBLIC_KEY_PATH = "~/.ssh/id_ed25519.pub"
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.provision "file", source: PUBLIC_KEY_PATH, destination: "/home/vagrant/.ssh/id.pub"
  	config.vm.define "checkmk_server" do |checkmk|
		checkmk.vm.box = "ubuntu/xenial64"
		checkmk.vm.hostname = "server"
		checkmk.vm.network "private_network", ip:"192.168.123.100", nic_type: "virtio"
		checkmk.vm.provider "virtualbox" do |vb|
			vb.memory = "4096"  
			vb.cpus = "2"
		end  
		checkmk.vm.provision "shell", inline: <<-SHELL
			cat /home/vagrant/.ssh/id.pub >> /home/vagrant/.ssh/authorized_keys
			exit
		SHELL
	end
	config.vm.define "checkmk_lx_client" do |client|
		client.vm.box = "ubuntu/xenial64"
		client.vm.hostname = "client"
		client.vm.network "private_network", ip:"192.168.123.101" 
		client.vm.provider "virtualbox" do |vb|
			vb.memory = "512"  
		end 
		client.vm.provision "shell", inline: <<-SHELL
			cat /home/vagrant/.ssh/id.pub  >> /home/vagrant/.ssh/authorized_keys >> /home/vagrant/.ssh/authorized_keys
			exit
		SHELL
	end  
    # config.vm.define "clientwindows" do |client|
    #     client.vm.box = "mwrock/Windows2016"
    #     client.vm.hostname = "clientwindows"
    #     client.vm.network "private_network", ip:"192.168.123.102" 
    #     client.vm.provider "virtualbox" do |vb|
    #         vb.memory = "512"  
    #     end 
    # end  
 end