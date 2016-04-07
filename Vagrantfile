# -*- mode: ruby -*-
# vi: set ft=ruby :

$add_public_key = <<EOF1
echo Add Public Key
mkdir /root/.ssh
touch /root/.ssh/authorized_keys
chmod 755 /root/.ssh
chmod 644 /root/.ssh/authorized_keys
echo '#{File.read("#{Dir.home}/VagrantVM/apache/Vagrantconfig/keys/id-rsa.pub")}' >> /root/.ssh/authorized_keys
EOF1

$add_names_hosts = <<EOF2
echo Add name hosts
echo '#{File.read("#{Dir.home}/VagrantVM/apache/Vagrantconfig/hostsnames")}' >> /etc/hosts
EOF2

Vagrant.configure(2) do |config|
  config.vm.define :node1 do |node1|
    node1.vm.box = "centos/7"
    node1.vm.network "private_network", ip: "192.168.50.2"
    node1.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    node1.vm.provision :shell, :inline => $add_public_key
    node1.vm.provision :shell, :inline => $add_names_hosts
  end
end
