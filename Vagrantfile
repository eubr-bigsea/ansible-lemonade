# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2" # Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
ANSIBLE_TAGS = ENV['ANSIBLE_TAGS']

$ansible_raw_arguments = ['-T 30', '-e "ansible_user=vagrant pipelining=True"']

$ansible_groups = {
	"lemonade" => ["lemonade"],
}

$apt_proxy = "echo 'Acquire::http { Proxy \"http://roadrash:3142\"; }; Acquire::https::Proxy \"false\";' > /etc/apt/apt.conf.d/01proxy"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.define "lemonade" do |l|
    l.vm.hostname = "lemonade"
    l.vm.box = "cbednarski/ubuntu-1604"

    l.vm.network "forwarded_port", guest: 80, host: 8080
    l.vm.network "forwarded_port", guest: 3000, host: 3000

    l.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    #APT Proxy
    #l.vm.provision "shell", inline: $apt_proxy

    l.vm.provision "ansible" do |ansible|
      ansible.tags = ANSIBLE_TAGS
      ansible.raw_arguments = $ansible_raw_arguments
      ansible.groups =  $ansible_groups
      ansible.playbook = "lemonade.yml"
    end
  end
end
