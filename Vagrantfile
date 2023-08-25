# -*- mode: ruby -*-
# vi: set ft=ruby :

$install_ansible = <<-ANSIBLE
sudo apt install software-properties-common -y
sudo add-apt-repository --yes --update ppa:ansible/ansible -y
sudo apt install ansible -y
ANSIBLE

Vagrant.configure("2") do |config|

  if Vagrant.has_plugin? "vagrant-vbguest"
    config.vbguest.no_install  = true
    config.vbguest.auto_update = false
    config.vbguest.no_remote   = true
  end

  config.vm.define :clienteUbuntu1 do |clienteUbuntu1|
    clienteUbuntu1.vm.box = "bento/ubuntu-22.04"
    clienteUbuntu1.vm.network :private_network, ip: "192.168.100.2"
    clienteUbuntu1.vm.hostname = "clienteUbuntu1"
  end

  config.vm.define :servidorUbuntu0 do |servidorUbuntu0|
    servidorUbuntu0.vm.box = "bento/ubuntu-22.04"
    servidorUbuntu0.vm.network :private_network, ip: "192.168.100.3"
    servidorUbuntu0.vm.hostname = "servidorUbuntu0"
    servidorUbuntu0.vm.provision "shell", inline: $install_ansible
    servidorUbuntu0.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "master-playbook_ach.yml"
    end
  end

  config.vm.define :servidorUbuntu1 do |servidorUbuntu1|
    servidorUbuntu1.vm.box = "bento/ubuntu-22.04"
    servidorUbuntu1.vm.network :private_network, ip: "192.168.100.6"
    servidorUbuntu1.vm.hostname = "servidorUbuntu1"
    servidorUbuntu1.vm.provision "shell", inline: $install_ansible
    servidorUbuntu1.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "master-playbook_gen.yml"
    end
  end

  config.vm.define :servidorUbuntu2 do |servidorUbuntu2|
    servidorUbuntu2.vm.box = "bento/ubuntu-22.04"
    servidorUbuntu2.vm.network :private_network, ip: "192.168.100.7"
    servidorUbuntu2.vm.hostname = "servidorUbuntu2"
    servidorUbuntu2.vm.provision "shell", inline: $install_ansible
    servidorUbuntu2.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "master-playbook_gen.yml"
    end
  end

  config.vm.define :servidorUbuntu3 do |servidorUbuntu3|
    servidorUbuntu3.vm.box = "bento/ubuntu-22.04"
    servidorUbuntu3.vm.network :private_network, ip: "192.168.100.8"
    servidorUbuntu3.vm.hostname = "servidorUbuntu3"
    servidorUbuntu3.vm.provision "shell", inline: $install_ansible
    servidorUbuntu3.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "master-playbook_gen.yml"
    end
  end
end