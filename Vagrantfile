$script = <<SCRIPT

set -e

cp -Rv /vagrant/openvpn /etc/openvpn &&
apt-get update -y && 
apt-get dist-upgrade -y &&
apt-get install -y openvpn iftop iotop &&
echo -en "\nnet.ipv4.ip_forward = 1\n" >> /etc/sysctl.conf &&
reboot

SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provision "shell", inline: $script

  # SET THIS TO YOUR OWN PREFERENCE!
  config.vm.network "public_network", bridge: "eth0", ip: "192.168.1.2"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "256"
  end
end
