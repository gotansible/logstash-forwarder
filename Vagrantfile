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
			ansible.playbook = "test.yml"
		end
	end

end
