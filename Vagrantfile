Vagrant.configure("2") do |config|
    config.vm.define "open5gs-build"
    config.vm.box = "fedora/34-cloud-base"
    config.vm.provider :libvirt do |libvirt|
      libvirt.cpus = 4
      libvirt.memory = 2048
    end
end
