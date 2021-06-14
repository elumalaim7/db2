
Vagrant.configure("2") do |config|

  # RedHat 6.5
  config.vm.define "redhat", primary: true do |redhat|
    redhat.vm.box = "generic/rhel7"
    redhat.vm.hostname = "redhat"
    redhat.vm.network "private_network", ip: "192.168.56.20"
    redhat.vm.network "forwarded_port", guest: 50000, host: 50000
    redhat.vm.provider "virtualbox" do |v|
        v.customize [ "modifyvm", :id, "--cpus", "1" ]
        v.customize [ "modifyvm", :id, "--memory", "1024" ]
    end
  end
end
