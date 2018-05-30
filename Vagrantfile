# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

require 'vagrant-openstack-provider'
Vagrant.configure('2') do |config |
    config.ssh.username = 'ubuntu'
    config.ssh.private_key_path = "C:/Users/teresa lopez/.ssh/id_rsa"
    config.vm.provider :openstack do |os, override|
      os.identity_api_version = ENV['OS_IDENTITY_API_VERSION']
      os.openstack_auth_url = ENV['OS_AUTH_URL']
      os.domain_name        = ENV['OS_DOMAIN_NAME']
      os.username           = ENV['OS_USERNAME']
      os.password           = ENV['OS_PASSWORD']
      os.tenant_name        = ENV['OS_TENANT_NAME']
      os.project_name       = ENV['OS_PROJECT_NAME']
      os.keypair_name       = ENV['OS_KEY_PAIR_NAME']
      os.region             = ENV['OS_REGION_NAME']
      os.image              = ENV['OS_IMAGE']
    end

   config.vm.define 'tl-server1' do |s|
    s.vm.provider :openstack do |os, override|
      os.server_name = 'tl-gocd-vm-1'
      os.flavor = ENV['OS_FLAVOR_NAME']
      override.vm.synced_folder '.', '/vagrant', disabled: true
    end
  end
  config.vm.define 'tl-server2' do |s|
    s.vm.provision "docker"
    s.vm.provider :openstack do |os, override|
      os.server_name = 'tl-gocd-vm-2'
      os.flavor = ENV['OS_FLAVOR']
      override.vm.synced_folder '.', '/vagrant', disabled: true
    end
  end
end
