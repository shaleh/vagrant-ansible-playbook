vagrant-ansible-playbook
========================

Run a Ansible playbook using the Vagrant inventory if present other by looking
at an 'inventory' file in the current directory.

Placing a section like the following in your `Vagrantfile` will enable the
generation of an Ansible compatible inventory file.

    config.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "provision.yaml"
    end

This is what I use for the provision step. It is a simple ping.

    ---
    - hosts: all
      tasks:
        - name: Dummy
          ping:

