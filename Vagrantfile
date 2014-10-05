# -*- mode: ruby -*-

# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
cat << EOF >> /etc/hosts
172.29.236.2 021579-infra01
172.29.236.3 021579-infra02
172.29.236.4 021579-infra03
172.29.236.5 021579-logging01
172.29.236.6 021579-network01
172.29.236.10 021579-compute001
EOF
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"

  # Turn off shared folders
  config.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true

  # Begin infra1
  config.vm.define "infra1" do |infra1_config|
    infra1_config.vm.hostname = "021579-infra01"

    infra1_config.vm.provision "shell", inline: $script

    # eth1
    infra1_config.vm.network "private_network", ip: "172.29.236.2"
    # eth2
    infra1_config.vm.network "private_network", ip: "172.29.240.2"
    # eth3
    infra1_config.vm.network "private_network", ip: "172.29.236.12"
    
    infra1_config.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "2048"
        v.vmx["numvcpus"] = "2"
    end

    infra1_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "2048"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    infra1_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/base.yml"
    end
  end
  # End infra1
  
  # Begin infra2
  config.vm.define "infra2" do |infra2_config|
    infra2_config.vm.hostname = "021579-infra02"

    infra2_config.vm.provision "shell", inline: $script

    # eth1
    infra2_config.vm.network "private_network", ip: "172.29.236.3"
    # eth2
    infra2_config.vm.network "private_network", ip: "172.29.240.3"
    # eth3
    infra2_config.vm.network "private_network", ip: "172.29.236.13"
        
    infra2_config.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "2048"
        v.vmx["numvcpus"] = "2"
    end

    infra2_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "2048"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    infra2_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/base.yml"
    end
  end
  # End infra2
  
  # Begin infra3
  config.vm.define "infra3" do |infra3_config|
    infra3_config.vm.hostname = "021579-infra03"

    infra3_config.vm.provision "shell", inline: $script

    # eth1
    infra3_config.vm.network "private_network", ip: "172.29.236.4"
    # eth2
    infra3_config.vm.network "private_network", ip: "172.29.240.4"
    # eth3
    infra3_config.vm.network "private_network", ip: "172.29.236.14"
        
    infra3_config.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "2048"
        v.vmx["numvcpus"] = "2"
    end

    infra3_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "2048"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    infra3_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/base.yml"
    end
  end
  # End infra3

  # Begin logging1
  config.vm.define "logging1" do |logging1_config|
    logging1_config.vm.hostname = "021579-logging01"

    logging1_config.vm.provision "shell", inline: $script

    # eth1
    logging1_config.vm.network "private_network", ip: "172.29.236.5"
    # eth2
    logging1_config.vm.network "private_network", ip: "172.29.240.5"
    # eth3
    logging1_config.vm.network "private_network", ip: "172.29.236.15"
        
    logging1_config.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "1024"
        v.vmx["numvcpus"] = "1"
    end

    logging1_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "1024"]
        v.customize ["modifyvm", :id, "--cpus", "1"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    logging1_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/base.yml"
    end
  end
  # End logging1

# Begin network1
  config.vm.define "network1" do |network1_config|
    network1_config.vm.hostname = "021579-network01"

    network1_config.vm.provision "shell", inline: $script

    # eth1
    network1_config.vm.network "private_network", ip: "172.29.236.6"
    # eth2
    network1_config.vm.network "private_network", ip: "172.29.240.6"
    # eth3
    network1_config.vm.network "private_network", ip: "172.29.236.16"
        
    network1_config.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "2048"
        v.vmx["numvcpus"] = "2"
    end

    network1_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "2048"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    network1_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/base.yml"
    end
  end
  # End network1
 
   # Begin compute1
  config.vm.define "compute1" do |compute1_config|
    compute1_config.vm.hostname = "021579-compute001"

    compute1_config.vm.provision "shell", inline: $script

    # eth1
    compute1_config.vm.network "private_network", ip: "172.29.236.10"
    # eth2
    compute1_config.vm.network "private_network", ip: "172.29.240.10"
    # eth3
    compute1_config.vm.network "private_network", ip: "172.29.236.20"
    
    compute1_config.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "2048"
        v.vmx["numvcpus"] = "2"
    end

    compute1_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "2048"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    compute1_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/compute_update.yml"
    end
  end
  # End compute1
end