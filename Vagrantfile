Vagrant.configure("2") do |config|
  config.vm.define "k8s-master"
  config.vm.box = "debian/bookworm64"
  config.vm.box_version = "12.20250126.1"
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
