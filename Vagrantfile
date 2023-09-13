Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
    config.vm.network "forwarded_port", guest: 3000, host: 3000
  
    config.vm.provision "docker" do |d|
      d.build_image "/vagrant", args: "-t my-node-app"
      d.run "my-node-app", args: "-p 3000:3000"
    end
  
    config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y docker.io
    SHELL
  end
  