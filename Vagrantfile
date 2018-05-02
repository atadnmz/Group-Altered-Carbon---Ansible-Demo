Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  config.vm.provision "shell", inline: "sudo apt-get install software-properties-common;
  sudo apt-add-repository ppa:ansible/ansible; sudo apt-get update; sudo apt-get install ansible -y"
  #config.vm.provision "shell", inline: "sudo yum install python-pip python-devel python ; sudo pip install pip --upgrade ; sudo pip install ansible==1.9.2"
  #config.vm.provision "shell", inline: "ansible-galaxy install geerlingguy.java"

  config.vm.provision 'preemptively give others write access to /etc/ansible/roles', type: :shell, inline: "sudo mkdir /etc/ansible/roles -p ; sudo chmod o+w /etc/ansible/roles "

  config.vm.provision 'ansible', type: :ansible_local do |ansible|
    ansible.galaxy_role_file = 'requirements.yml'
    ansible.galaxy_roles_path = '/etc/ansible/roles'
    ansible.galaxy_command = 'ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path}'
    ansible.playbook = 'playbook.yml'
    ansible.inventory_path = "hosts"
  end

  # config.vm.provision :ansible_local do |ansible|
  #   ansible.playbook = "playbook.yml"
  #   #ansible.galaxy_command = "sudo ansible-galaxy install geerlingguy.git"
  #   #ansible.galaxy_command = "sudo ansible-galaxy install --force geerlingguy.mysql"
  #   #ansible.galaxy_command = "sudo ansible-galaxy install --force  williamyeh.oracle-java"
  #   ansible.galaxy_roles_path= "/Users/onur.elbirlik/Desktop/AlteredCarbon/"
  #   ansible.galaxy_role_file = "requirements.yml"
  #   ansible.inventory_path = "hosts"
  #   #ansible.galaxy_command = "sudo ansible-galaxy install -r /Users/onur.elbirlik/Desktop/AlteredCarbon/requirements.yml"
  # end
end
  config.vm.define "ansible-master" do |test|
    test.vm.box = "ubuntu/trusty64"
    test.vm.hostname = "ansible-master.local"
    test.vm.network "private_network", ip: "192.168.99.10"
  end

  config.vm.define "mysql1" do |test|
    test.vm.box = "ubuntu/trusty64"
    test.vm.hostname = "mysql1.local"
    test.vm.network "private_network", ip: "192.168.99.11"
  end

  config.vm.define "git1" do |test|
    test.vm.box = "ubuntu/trusty64"
    test.vm.hostname = "git1.local"
    test.vm.network "private_network", ip: "192.168.99.12"
  end

  config.vm.define "oracleJDK1" do |test|
    test.vm.box = "ubuntu/trusty64"
    test.vm.hostname = "oracleJDK1.local"
    test.vm.network "private_network", ip: "192.168.99.13"
  end

end
