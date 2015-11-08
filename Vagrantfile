# -*- mode: ruby -*-
# # vi: set ft=ruby :

Vagrant.configure("2") do |config|

	# Define the CoreOS box
	config.vm.box = "coreos-stable"
	config.vm.box_url = "http://stable.release.core-os.net/amd64-usr/current/coreos_production_vagrant.json"

	# Define a static IP
	config.vm.network "private_network",
		ip: "33.33.33.77"

	# Share the current folder via NFS
	config.vm.synced_folder ".", "/home/core/sites",
		id: "core",
                nfs_version: "4",
                :nfs => true,
		:mount_options => ['nolock,noatime']

	# Provision docker with shell
	# config.vm.provision
	config.vm.provision "shell",
		path: ".coreos-devenv/scripts/provision-docker.sh"
	
	# Fix ssh issue
	config.ssh.insert_key = false
end
