# -- mode: ruby --
 # vi: set ft=ruby :0

 Vagrant.configure("2") do |config|
  disco = ".vagrant/disco1.vdi"
  disco2 = ".vagrant/disco2.vdi"
  disco3=".vagrant/disco3.vdi"  
  config.vm.box = "debian/buster64"
  config.vm.hostname = "Almacenamiento"
  config.vm.network :public_network,:bridge=>"wlp1s0"   
  config.vm.provider :virtualbox do |v|
    if not File.exist?(disco)
      v.customize ["createhd", "--filename", disco, "--size", 1 *  1024]
    end
      v.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", 1,"--device", 0, "--type", "hdd", "--medium", disco]
    if not File.exist?(disco2)
      v.customize ["createhd", "--filename", disco2, "--size", 1 * 1024]
    end
      v.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", 2,"--device", 0, "--type", "hdd", "--medium", disco2] 
    if not File.exist?(disco3)
      v.customize ["createhd", "--filename", disco3, "--size", 1 *  1024]
    end
      v.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", 3,"--device", 0, "--type", "hdd", "--medium", disco3]

  config.vm.provision "shell", run: "always",
    inline: "sudo apt-get install -y mdadm"
  end
 end

