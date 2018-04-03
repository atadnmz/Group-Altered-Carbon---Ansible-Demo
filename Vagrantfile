Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  config.vm.provision "shell", inline: "sudo apt-get install software-properties-common;
  sudo apt-add-repository ppa:ansible/ansible; sudo apt-get update; sudo apt-get install ansible -y"
#config.vm.provision "shell", inline: "sudo yum install python-pip python-devel python ; sudo pip install pip --upgrade ; sudo pip install ansible==1.9.2"
  #config.vm.provision "shell", inline: "ansible-galaxy install geerlingguy.java"
  config.vm.provision :ansible_local do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.galaxy_command = "sudo ansible-galaxy install geerlingguy.mysql"
    #ansible.galaxy_command = "ansible-galaxy install -r requirements.yml"
    ansible.galaxy_roles_path= "/Users/onur.elbirlik/Desktop/AlteredCarbon/"
    ansible.galaxy_role_file = "requirements.yml"
  end
end
  config.vm.define "test" do |test|
    test.vm.box = "ubuntu/trusty64"
    test.vm.hostname = "test.local"
    test.vm.network "private_network", ip: "192.168.99.10"
  end

  config.vm.define "database" do |test|
    test.vm.box = "ubuntu/trusty64"
    test.vm.hostname = "database.local"
    test.vm.network "private_network", ip: "192.168.99.11"
  end

end
