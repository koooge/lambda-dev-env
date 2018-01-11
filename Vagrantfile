Vagrant.configure("2") do |config|
  config.vm.box = "mvbcoding/awslinux"

  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = "1"
  end
  config.vm.provision :shell, privileged: false, inline: $script
end

$script = <<SCRIPT
sudo yum update -y -q
sudo yum install -y -q ntp git wget curl zip unzip vim tig jq tree
sudo pip install -U -q awscli

# my dotfiles
curl -sS -L raw.github.com/koooge/dotfiles/master/install.sh | bash &> /dev/null

# node
NVM_VERSION=v0.33.8
NODE_VERSION=v6.10.3
curl -sS -o- https://raw.githubusercontent.com/creationix/nvm/${NVM_VERSION}/install.sh | bash
cat << EOF >> ~/.bashrc
export NVM_DIR=~/.nvm
[ -s "${NVM_DIR}/nvm.sh" ] && . "${NVM_DIR}/nvm.sh"
EOF
source ~/.bashrc
nvm install ${NODE_VERSION} &> /dev/null
nvm use ${NODE_VERSION}
nvm alias default ${NODE_VERSION}
SCRIPT
