Vagrant.configure("2") do |config|
  config.vm.box = "mvbcoding/awslinux"

  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = "1"
  end
  #config.vm.provision :shell, inline: $script
end

$script = <<SCRIPT
apt-get update
apt-get upgrade -y
apt-get install -y ntp
SCRIPT
