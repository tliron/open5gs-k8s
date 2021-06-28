Vagrant.configure("2") do |config|
    config.vm.define "openg5s-build"
    config.vm.box = "fedora/34-cloud-base"
    #config.vm.box = "centos/stream8"
    config.vm.provider :libvirt do |libvirt|
      libvirt.cpus = 4
      libvirt.memory = 2048
    end
    #config.vm.provision :shell, path: "install"
end
