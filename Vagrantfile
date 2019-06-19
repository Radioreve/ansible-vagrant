# This file describes the virtual machines 
# That represent our lab environment

VAGRANT_VERSION = "2"

# Ensure people using this script will the minimum required version to execute it
Vagrant.require_version ">= 2.0.0"

Vagrant.configure(VAGRANT_VERSION) do |config|
  config.vm.define :haproxy do |guest|
   guest.vm.hostname = "haproxy"
   guest.vm.box = "ubuntu/trusty64"
   guest.vm.network :private_network, ip: "10.0.0.10"
   guest.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/haproxy.yml"
    end
  end

  config.vm.define :webserver1 do |guest|
    guest.vm.hostname = "web1"
    guest.vm.box = "ubuntu/trusty64"
    guest.vm.network :private_network, ip: "10.0.0.11"
  end

  config.vm.define :webserver2 do |guest|
    guest.vm.hostname = "web2"
    guest.vm.box = "ubuntu/trusty64"
    guest.vm.network :private_network, ip: "10.0.0.12"
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = './ansible/install.yml'
  end

end
