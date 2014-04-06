# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/ubuntu-13.10"
  config.vm.hostname = "jenkins-saucy64"

  # forward traffic to Tomcat
  config.vm.network :forwarded_port, guest: 8080, host: 8080

  config.vm.provision :ansible do |ansible|
    ansible.sudo = true
    ansible.playbook = "jenkins-saucy64.yml"
    ansible.extra_vars = {
      # speciy a custom Jenkins version
      #jenkins_war_version: "1.532.2"
      # ...or the latest version
      #jenkins_war_version: "latest"

      # specify a custom apt mirror
      #apt_mirror_url: "mirror://mirrors.ubuntu.com/mirrors.txt"
    }
  end

  config.vm.provider :virtualbox do |vbox|
    # Jenkins require a bit of memory
    vbox.memory = 768
  end
end
