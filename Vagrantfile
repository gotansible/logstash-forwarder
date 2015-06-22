# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

	config.vm.define "server" do |server|
		server.vm.box = "hashicorp/precise64"
		server.vm.hostname = "server"
		server.vm.provision :ansible do |ansible|
			ansible.playbook = "test-server.yml"
		end
		server.vm.network "private_network", ip: "192.168.50.9"
		server.vm.synced_folder "keygen", "/etc/pki/selfsign"

		# supposedly enables chmod on a synced folder, however requires 
		# vagrant to ask you for sudo permissions
		#, type: :nfs, map_uid: 0, map_gid: 0
	end

	config.vm.define "client" do |client|
		#client.vm.box = "hashicorp/precise64"
		client.vm.box = "chef/centos-6.5"
		client.vm.hostname = "client"
		client.vm.provision :ansible do |ansible|
			ansible.playbook = "test.yml"
			ansible.extra_vars = {
			}
		end
		client.vm.network "private_network", ip: "192.168.50.20"
	end
end
