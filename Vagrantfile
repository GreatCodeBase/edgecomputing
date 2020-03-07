Vagrant.configure("2") do |config|
  config.vm.boot_timeout = 2800
  #config.ssh.username = "vagrant"
  #config.ssh.password = "vagrant"
  config.vm.define :node1 do |n1|
    n1.vm.provider "virtualbox" do |v|
          unless File.exist?('secondDisk.vdi')
            v.customize ['createhd', '--filename', 'secondDisk.vdi', '--size', 10 * 1024]
          end
          v.customize ['storageattach', :id,  '--storagectl', 'SCSI', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', 'secondDisk.vdi']
          v.customize ["modifyvm", :id, "--name", "node1", "--memory", "1024", "--uartmode1", "disconnected"]
    end
    n1.vm.box = "ubuntu1804"
    n1.vm.hostname = "node1"
    n1.vm.network:public_network,ip:"192.168.0.233"
  end

  config.vm.define :node2 do |n2|
    n2.vm.provider "virtualbox" do |v|
          unless File.exist?('thirdDisk.vdi')
            v.customize ['createmedium', '--filename', 'thirdDisk.vdi','--size', 10 * 1024]
          end
          v.customize ['storageattach', :id,  '--storagectl', 'SCSI', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', 'thirdDisk.vdi']
          v.customize ["modifyvm", :id, "--name", "node2", "--memory", "1024", "--uartmode1", "disconnected"]
    end
    n2.vm.box = "ubuntu1804"
    n2.vm.hostname = "node2"
    n2.vm.network:public_network, ip:"192.168.0.234"
  end

  config.vm.define :node3 do |n3|
    n3.vm.provider "virtualbox" do |v|
          unless File.exist?('fourthDisk.vdi')
            v.customize ['createhd', '--filename', 'fourthDisk.vdi', '--size', 10 * 1024]
          end
          v.customize ['storageattach', :id,  '--storagectl', 'SCSI', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', 'fourthDisk.vdi']
          v.customize ["modifyvm", :id, "--name", "node3", "--memory", "1024", "--uartmode1", "disconnected"]
    end
    n3.vm.box = "ubuntu1804"
    n3.vm.hostname = "node3"
    n3.vm.network:public_network, ip:"192.168.0.235"
  end
end