# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.define 'ns1' do |ns|
    ns.vm.hostname = 'ns1'
    ns.vm.network 'private_network', ip: '10.0.0.11'
  end

  config.vm.define 'ns2' do |ns|
    ns.vm.hostname = 'ns2'
    ns.vm.network 'private_network', ip: '10.0.0.12'
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'site.yml'
    ansible.limit = 'all'
    ansible.sudo = true
    ansible.extra_vars = {
      ansible_ssh_user: 'vagrant'
    }
    ansible.groups = {
      'dns_servers' => ['ns1', 'ns2'],
      'cdn_servers' => ['ns1', 'ns2']
    }
  end
end
