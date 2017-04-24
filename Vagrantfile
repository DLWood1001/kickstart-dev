# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
   config.vm.define "kickstart" do |ks|
      ks.vm.box = "bento/fedora-25"
      # ks.vm.provider "libvirt"

      # ks.vm.synced_folder ".", "/vagrant",
      #    disabled: false,
      #    create: true,
      #    type: "nfs",
      #    nfs: true,
      #    nfs_udp: false,
      #    nfs_version: 3
   
      ks.vm.network "forwarded_port",
         guest: 80,
         host: 8080

      ks.vm.network "private_network",
         ip: "192.168.0.101",
         mask: "255.255.255.0"

      ks.vm.provision "boostrap",
         type: "ansible",
         playbook: "provision/pb_bootstrap.yaml"

      ks.vm.provision "httpd",
         type: "ansible",
         playbook: "provision/pb_install_httpd.yaml"
  end
end
