Vagrant.configure("2") do |config|  
    config.vm.define :dockernode do |dockernode|
        dockernode.vm.provider :virtualbox do |v|
            v.name = "dockernode"
            v.customize [
                "modifyvm", :id,
                "--name", "dockernode",
                "--memory", 5120,
                "--natdnshostresolver1", "on",
                "--cpus", 2,
            ]
        end
        dockernode.vm.box = "bento/oraclelinux-8"
        dockernode.vm.network :private_network, ip: "192.168.30.20"
        dockernode.ssh.forward_agent = true
        dockernode.vm.hostname = "dockernode"  # Correct placement of hostname
        dockernode.vm.provision "shell", inline: <<-SHELL
            sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
            systemctl restart sshd.service
        SHELL
        # dockernode.vm.provision "file", source: "id_ed25519.pub", destination: "~/.ssh/authorized_keys"
    end

    config.vm.define "slave" do |slave|
        slave.vm.provider :virtualbox do |v|
            v.name = "slave"
            v.customize [
                "modifyvm", :id,
                "--name", "slave",
                "--memory", 512,
                "--natdnshostresolver1", "on",
                "--cpus", 1,
            ]
        end
        slave.vm.box = "bento/oraclelinux-8"
        slave.vm.network :private_network, ip: "192.168.30.21"
        slave.ssh.forward_agent = true
        slave.vm.hostname = "slave"  # Correct placement of hostname
        slave.vm.provision "shell", inline: <<-SHELL
            sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
            systemctl restart sshd.service
        SHELL
        # slave.vm.provision "file", source: "id_ed25519.pub", destination: "~/.ssh/authorized_keys"
    end
end


#Vagrant.configure("2") do |config|
#    config.vm.define "apps" do |apps|
#        apps.vm.provider :virtualbox do |v|
#            v.name = "apps"
#            v.customize [
#                "modifyvm", :id,
#                "--name", "apps",
#                "--memory", 512,
#                "--natdnshostresolver1", "on",
#                "--cpus", 1,
#            ]
#        end
#
#        apps.vm.box = "centos/7"
#        apps.vm.network :private_network, ip: "192.168.30.3"
#        apps.ssh.forward_agent = true
#		config.vm.provision "shell", inline: <<-SHELL
#		sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
#		systemctl restart sshd.service
#		SHELL
#		config.vm.hostname = "apps"
##		config.ssh.private_key_path = ".vagrant/machines/slave/virtualbox/private_key"
##		config.vm.provision "file", source: "id_ed25519.pub", destination: "~/.ssh/authorized_keys"
#    end
#end
