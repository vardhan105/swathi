 Vagrant.configure(2) do | config |
    config.vm.define "jenkinsserver" do | jenkinsmaster |
        jenkinsmaster.vm.box = "ubuntu/jammy64"
        jenkinsmaster.vm.network "private_network", ip: "192.168.11.10"
        jenkinsmaster.vm.network "forwarded_port", guest: 8080, host: 8081
        jenkinsmaster.vm.hostname = "jenkinsserver"
        jenkinsmaster.vm.provider "virtualbox" do | vb |
            vb.cpus = 2
            vb.memory = 2048
            vb.name = "jenkinsserver"
        end
    end
    %w{jenkinsslave1 jenkinsslave2}.each_with_index do | nodename, index |
        config.vm.define nodename do | slaveNode |
            slaveNode.vm.box = "ubuntu/jammy64"
            slaveNode.vm.network "private_network", ip: "192.168.11.#{index+11}"
            slaveNode.vm.hostname = nodename
            slaveNode.vm.provider "virtualbox" do | vb |
                vb.cpus = 2
                vb.memory = 2048
                vb.name = nodename
            end
        end
    end
  end