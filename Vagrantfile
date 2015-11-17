# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.provider :libvirt do |libvirt|
    libvirt.memory = 2048
    libvirt.cpus = 2
  end

  config.vm.define 'storyboard' do |machine|
    machine.vm.hostname = 'storyboard'
    machine.vm.network "private_network", ip: "192.168.77.60"

    machine.vm.provision :ansible do |ansible|
      ansible.playbook = "instance-config.yml"
      ansible.sudo = true
      ansible.verbose = 'vvvv'

      ansible.extra_vars = {
        fqdn: '192.168.77.60.xip.io'
      }

      ansible.groups = {
        "storyboard" => ["storyboard"],
      }

      # Disable default limit (required with Vagrant 1.5+)
      ansible.limit = 'all'

    end
  end

end
