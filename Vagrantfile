# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("1") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.usable_port_range = (62222..65535) # Solve used port issue
  config.vm.network "forwarded_port", guest: 22, host: basePort, id: "ssh", auto_correct: true

  # Configure VM resources
  # This is provider specific!
  # See also, https://www.vagrantup.com/docs/providers/virtualbox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = 8
  end

  # Master node unique setup:
  #
  # - hostname
  # - Fixed IP for the private network, 10.8.8.2
  config.vm.define "ubuntuWorker" do |master|
    master.vm.hostname = "ubuntuWorker"
    master.vm.network "private_network", ip: "10.8.8.2"
  end

  # VM provisioning using ansible
  # In ubuntu 20.04 there is no /usr/bin/python, added extra var to fix this
  # Note that it is better to also install ansible at host using pip3 to avoid
  # other problems also... I guess we would not even need the extra var.
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provision.yml"
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3"
    }
  end
end
