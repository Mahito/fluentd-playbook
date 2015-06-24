VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |global_config|
  global_config.vm.box     = 'ubuntu14.04-base_20141127'
  global_config.vm.box_url = 'https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box'

  global_config.vm.define :tdagent do |config|
    config.vm.hostname = 'tdagent'
    config.vm.network :private_network, ip: '192.168.10.11'
    config.vm.provider :virtualbox do |v|
      v.name = config.vm.hostname
      v.cpus   = 1
      v.memory = 1024
    end
    config.vm.provision :ansible do |ansible|
      ansible.playbook = 'td-agent.yml'
      ansible.verbose  = 'vvv'
    end
  end
end
