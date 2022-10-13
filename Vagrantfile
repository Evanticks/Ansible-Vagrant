Vagrant.configure("2") do |config|
    config.vm.define :nodo1 do |nodo1|
      nodo1.vm.box = "debian/bullseye64"
      nodo1.vm.hostname= "nodo1"
      nodo1.vm.synced_folder ".", "/vagrant", disabled: true
      nodo1.vm.network :public_network,
        :dev => "br0",
        :mode => "bridge",
        :type => "bridge",
        use_dhcp_assigned_default_route: true
      nodo1.vm.network :private_network,
        :libvirt__network_name => "red1",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.10",
        :libvirt__forward_mode => "veryisolated"
    end
    config.vm.define :nodo2 do |nodo2|
      nodo2.vm.box = "debian/bullseye64"
      nodo2.vm.hostname = "nodo2"
      nodo2.vm.synced_folder ".", "/vagrant", disabled: true
      nodo2.vm.network :private_network,
        :libvirt__network_name => "red1",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.11",
        :libvirt__forward_mode => "veryisolated",
        use_dhcp_assigned_default_route: true
    end
end
