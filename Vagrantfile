Vagrant.configure("2") do |config|
    config.vm.box = "Skatteetaten/hashistack"
    config.vm.box_version = ">= 0.11, < 0.12"
    config.vm.boot_timeout = 600
    config.vm.provider "virtualbox" do |vb|
        vb.linked_clone = true
        vb.memory = 6144
        vb.cpus = 2
    end
    config.vm.provision "ansible_local" do |ansible|
        ansible.provisioning_path = "/vagrant/dev/ansible"
        ansible.playbook = "playbook.yml" # Note this playbook is, in this context, /ansible/playbook.yml
        ansible.raw_arguments = Shellwords.shellsplit(ENV["ANSIBLE_ARGS"]) if ENV["ANSIBLE_ARGS"]
    end
end