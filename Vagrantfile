Vagrant.require_version ">= 2.2.19"

Vagrant.configure("2") do |config|
	
	# Машина с kubernetes
	config.vm.define "kubernetes" do |kubernetes|
		kubernetes.vm.box = "debian/bookworm64"
		kubernetes.vm.box_version = "12.20240905.1"
		kubernetes.vm.disk :disk, size: "30GB", primary: true
		
		kubernetes.vm.provider "virtualbox" do |virtualbox|
			virtualbox.memory = "3000"
			virtualbox.cpus = 2
		end
	
		kubernetes.vm.network "private_network", ip: "192.168.56.100"
		kubernetes.vm.provision "ansible_local" do |ansible|
			ansible.install = true
			ansible.playbook = "./provision/playbook.yml"
		end
	end
	
 
end







