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
			ansible.playbook = "../logstash/test.yml"
		end
		server.vm.network "private_network", ip: "192.168.50.9"
	end

	config.vm.define "client" do |client|
		client.vm.box = "hashicorp/precise64"
		client.vm.hostname = "client"
		client.vm.provision :ansible do |ansible|
			ansible.playbook = "test.yml"
			ansible.extra_vars = {
				logstash_forwarder_logstash_server: "192.168.50.9",
				logstash_forwarder_logstash_server_port: "12345"
			}
		end
	end

end
