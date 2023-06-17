# Variables
var_box            = 'generic/oracle8'
var_mem_size       = 1024  # More would be better.
var_cpus           = 1
NUM_NODES          = 3
IP_NW              = "10.0.0."
IP_START           = 10

Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: <<-SHELL
      yum update -y
    SHELL
    config.vm.box = var_box
    config.vm.box_check_update = true

#    config.vm.define "ansible" do |ansible|
#      ansible.vm.hostname = "ansible"
#      ansible.vm.network "private_network", ip: IP_NW + "#{IP_START}"
#      ansible.vm.provider "virtualbox" do |vb|
#        vb.memory = var_mem_size
#        vb.cpus = var_cpus
#      end
#    end

    (1..NUM_NODES).each do |i|
      config.vm.define "patroni0#{i}" do |node|
        node.vm.hostname = "patroni0#{i}"
        node.vm.network "private_network", ip: IP_NW + "#{IP_START + i}"
        node.vm.provider "virtualbox" do |vb|
            vb.memory = var_mem_size
            vb.cpus = var_cpus
        end
      end
    end
  end
