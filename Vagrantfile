Vagrant.configure("2") do |config|
  config.vm.box = "devreactor/phpdevstack"
  config.vm.box_check_update = true

  config.vm.network "private_network", ip: "192.168.33.10"

  #This commands creates and syncs the folder devreactor on the host 
  #machine with the devreactor folder on the guest vm and is mounted
  #using the permission of the user devreactor on the guest vm
  config.vm.synced_folder "./devreactor", "/var/www/devreactor",
	owner: "devreactor",
	group: "devreactor",
	create: true,
	disabled: false	

  config.vm.provider "virtualbox" do |vb|
  #  vb.gui = true
     #VM Memory
     vb.memory = "2048"
     
     #Serial Port and Raw File Location
     vb.customize ["modifyvm", :id, "--uart1", "0x3f8", "4"]
     vb.customize ["modifyvm", :id, "--uartmode1", "file", File.join(Dir.pwd, "/ubuntu-bionic-18.04-cloudimg-console.log")]
   end
end