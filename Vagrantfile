# -*- mode: ruby -*-

# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
cat << EOF >> /etc/hosts
172.29.236.2 021579-infra01
172.29.236.5 021579-logging01
172.29.236.6 021579-storage01
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
        v.vmx["memsize"] = "5120"
        v.vmx["numvcpus"] = "2"
    end

    infra1_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "5120"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    end
    
    infra1_config.vm.provision "ansible" do |ansible|
    	ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        ansible.playbook = "provisioning/base.yml"
    end
  end
  # End infra1
  
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
        v.vmx["memsize"] = "3072"
        v.vmx["numvcpus"] = "2"
    end

    compute1_config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "3072"]
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