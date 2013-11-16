Vagrant.configure("2") do |config|
  config.vm.define :playbox do |config|
    config.vm.network :private_network, ip: "10.0.10.99"
    config.vm.box = "precise64-docker"
    config.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vbox.box"
    config.vm.provider :virtualbox do |vm|
      vm.customize [ "modifyvm", :id, "--memory", "1024", "--cpus", "2" ]
    end

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.inventory_path = "provisioning/ansible_hosts"
    end

    config.vm.synced_folder "~/repos/", "/mnt/repos"
  end
end
