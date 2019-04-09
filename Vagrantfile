IMAGE_NAME = "ubuntu/xenial64"
N = 1

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.ssh.private_key_path = ["~/.vagrant.d/insecure_private_key"]

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end

    config.vm.network :forwarded_port, guest: 22, host: 2222, host_ip: "0.0.0.0", id: "ssh", auto_correct: true

    (1..N).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = IMAGE_NAME
            node.vm.network "private_network", ip: "192.168.50.#{i + 10}"
            node.vm.hostname = "node-#{i}"
            
            end
        end
    end