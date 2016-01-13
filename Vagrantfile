Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.define :server do |srv|
    srv.vm.hostname = "graphite"
    srv.vm.network "private_network", ip: "192.168.33.10"
    srv.vm.network "forwarded_port", guest: 80, host: 8080
    srv.vm.provision "shell", path: "provision.sh"
  end
end
