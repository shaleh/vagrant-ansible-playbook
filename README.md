vagrant-ansible-playbook
========================

Run a Ansible playbook using the Vagrant inventory. `vagrant-ansible-playbook` is a drop in replacement for `ansible-playbook`
with the caveat that the inventory is already specified.

Ever wanted to spin a vagrant machine and then run a playbook against it? It is frustrating because to call `ansible-playbook`
all of the SSH information needs to be provided. This script solves that by reading in the values from the inventory Vagrant
makes for you.

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

