def genvm(config,hostname,ip_address,netmask,memory,cpus)
  config.vm.define "#{hostname}" do |vmachine|
    
    # -- Hostname configuration -- #
    vmachine.vm.hostname = "#{hostname}"

    # -- Network configuration -- #
    vmachine.vm.network "private_network", ip: "#{ip_address}", netmask: "#{netmask}"

    # -- Provider configuration -- #
    vmachine.vm.provider "virtualbox" do |provider|
      provider.memory = "#{memory}"
      provider.name = "#{hostname}"
      provider.cpus = "#{cpus}"
      provider.gui = true
    end
  end
end

Vagrant.configure("2") do |config|

  # * Operating system configuration * #
  # -- The operating system that will be used in this lab is Red Hat Enterprise Linux version 9. -- #"
  config.vm.box = "generic/rhel9"
  
  # * Virtual machine configuration * #
  vm_config = [
    { "hostname" => "servera", "ip_address" => "172.18.250.21", "netmask" => "255.255.255.0", "memory" => 2048, "cpus" => 1 },
    { "hostname" => "serverb", "ip_address" => "172.18.250.22", "netmask" => "255.255.255.0", "memory" => 2048, "cpus" => 1 },
    { "hostname" => "podman", "ip_address" => "192.0.24.150", "netmask" => "255.255.255.0", "memory" => 4096, "cpus" => 2 }
  ]
  
  # * This loop deploys the machines * #
  vm_config.each do |vmach|

    # This function generates the necesary virtual machines using the parameters provided in the vm_config array.
    genvm(config,vmach["hostname"],vmach["ip_address"],vmach["netmask"],vmach["memory"],vmach["cpus"])
  end
end
