Vagrant.configure(2) do config
  config.vm.box = debianbullseye64
  config.vm.hostname = k8s-master
  config.vm.network private_network, ip 192.168.56.10

  config.vm.provider virtualbox do vb
    vb.memory = 4096
    vb.cpus = 2
  end

  config.vm.provision ansible do ansible
    ansible.playbook = playbook.yml
    ansible.inventory_path = inventory.ini
    ansible.limit = all
  end
end
