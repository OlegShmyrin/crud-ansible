Vagrant.configure("2") do |config|

    (1..2).each do |i|

        config.vm.define "web-#{i}" do |conf|
            conf.vm.box = "ubuntu/focal64"
            conf.vm.hostname = "web-#{i}"
            #conf.vm.network "private_network", type: "dhcp"
            conf.vm.network "public_network", ip: "192.168.1.10#{i}", netmask: "255.255.255.0", virtualbox_intnet: "net-1", bridge: "wlp2s0" 
            #conf.vm.network "forwarded_port", guest: 80, host: 8080
            # ... other config
            
            conf.vm.provision "shell" do |s|
                ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa_no_pass.pub").first.strip
                s.inline = <<-SHELL
                    echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
                    echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
                SHELL
            # ...
            end
            conf.vm.provider "virtualbox" do |vb|
                vb.gui = false
                vb.memory = 512
                vb.cpus = 1
            end
            
        end
    end
    config.vm.define "db-mysql-1" do |conf|
            conf.vm.box = "ubuntu/focal64"
            conf.vm.hostname = "db-mysql-1"
            #conf.vm.network "private_network", type: "dhcp"
            conf.vm.network "public_network", ip: "192.168.1.110", netmask: "255.255.255.0", virtualbox_intnet: "net-1", bridge: "wlp2s0" 
            #conf.vm.network "forwarded_port", guest: 80, host: 8080
            # ... other config
            
            conf.vm.provision "shell" do |s|
                ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa_no_pass.pub").first.strip
                s.inline = <<-SHELL
                    echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
                    echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
                SHELL
            # ...
            end
            conf.vm.provider "virtualbox" do |vb|
                vb.gui = false
                vb.memory = 512
                vb.cpus = 1
            end
            
        end

end