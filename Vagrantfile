Vagrant.configure("2") do |config|
  config.vm.define "kubernetes"
  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "k8s-master"
  config.vm.network "private_network", ip: "192.168.56.10"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4096
    vb.cpus = 2
	vb.customize ["modifyvm", :id, "--paravirtprovider", "kvm"]
	vb.customize ["modifyvm", :id, "--rtcuseutc", "on"]
	vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
  end

  config.vm.provision "ansible_local" do |ansible|
	ansible.install = true
    ansible.playbook = "playbook.yml"
  end
end
