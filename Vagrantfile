Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
  end

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provision :docker
  config.vm.provision "pip-install", type: "shell", inline: "apt install -y python-pip"
  config.vm.provision "docker-compose-install", type: "shell", inline: "pip install docker-compose"
  config.vm.provision "docker-compose", type: "shell", inline: "docker-compose -f /vagrant/docker-compose.yml up -d", run: "always"

  config.vm.network :forwarded_port, guest: 8888, host: 8888
end
