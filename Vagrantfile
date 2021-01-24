Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.define "node_0" do |node|
    node.vm.network "private_network", ip: "10.0.10.2"
    node.vm.network "forwarded_port", guest: 2375, host: 2378
  end
  (1..2).each do |i|
    config.vm.define "node_#{i}" do |node|
      node.vm.network "private_network", ip: "10.0.10.#{2 + i}"
    end
  end
end
