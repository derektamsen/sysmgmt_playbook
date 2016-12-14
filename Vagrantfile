# This guide is optimized for Vagrant 1.7 and above.
# Although versions 1.6.x should behave very similarly, it is recommended
# to upgrade instead of disabling the requirement below.
Vagrant.require_version '>= 1.7.0'

Vagrant.configure(2) do |config|

  config.vm.box = 'ubuntu/yakkety64'

  config.vm.hostname = 'desktop'

  config.vm.provision 'ansible_local' do |ansible|
    ansible.verbose = true
    ansible.playbook = 'site.yml'
    ansible.limit = 'desktop'
    ansible.inventory_path = 'production'
  end
end
