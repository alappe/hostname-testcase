# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
Vagrant.require_version ">= 1.5.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.omnibus.chef_version = '12.5.1'
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, type: "dhcp"

  config.vm.provider 'virtualbox' do |v, override|
    v.name = "hostname-testcase"
    v.memory = 4096
    v.cpus = 1
  end

  config.berkshelf.enabled = true
  config.vm.provision 'chef_zero' do |chef|
    chef.verbose_logging = true
    chef.cookbooks_path = '.'
    chef.data_bags_path = "data_bags"
    chef.nodes_path = "nodes"
    chef.roles_path = "roles"
    chef.add_recipe "hostname"
  end
end
