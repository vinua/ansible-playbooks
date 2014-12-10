# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.define 'sirius' do |machine|
    machine.vm.hostname = 'sirius'
    machine.vm.network 'private_network', ip: '10.0.0.11'
  end

  config.vm.define 'canopus' do |machine|
    machine.vm.hostname = 'canopus'
    machine.vm.network 'private_network', ip: '10.0.0.12'
  end

  config.vm.define 'toliman' do |machine|
    machine.vm.hostname = 'toliman'
    machine.vm.network 'private_network', ip: '10.0.0.13'
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'provision.yml'
    ansible.sudo = true
    ansible.extra_vars = {
      ansible_ssh_user: 'vagrant'
    }
    ansible.groups = {
      'dns_servers' => ['sirius', 'canopus'],
      'proxy_servers' => ['sirius', 'canopus'],
      'docker_servers' => ['toliman']
    }
  end
end
