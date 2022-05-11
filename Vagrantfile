$script = <<-SCRIPT
apt-get update
apt-get install git docker docker-compose -y
systemctl enable docker && systemctl start docker
git clone https://github.com/EthicalObligation/htpc-download-box.git
chown -R vagrant:vagrant htpc-download-box
cd htpc-download-box
cp .env.example .env
docker-compose up -d
sleep 60
chown -R vagrant:vagrant /media
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.memory = 2048
  config.vm.provision "shell", inline: $script
  config.vm.network "public_network"
end
