Vagrant.configure(2) do |config|

    config.vm.define "symfony" do |symfony|
        # Base template for virtualbox, we use ubuntu 14.04 here
        symfony.vm.box = "ubuntu/trusty64"
        # Domain on which our application will respond later on
        symfony.vm.hostname  = "symfony.dev"
        # IP address will be used by the VM
        symfony.vm.network :private_network, ip: "192.168.33.151"
	
	# Tell vagrant to run ansible as a provisioner
        symfony.vm.provision :ansible do |ansible|
            # where the playbook is located
            ansible.playbook = "provisioning/playbook.yml"
        end
    end

    # Access the shared vagrant directory via NFS, otherwise slow on mac and windows
    config.vm.synced_folder ".", "/vagrant", type: "nfs"

    config.vm.provider "virtualbox" do |v|
        # tell virtualbox to give our machine 1 GB RAM and 2 Cores
        v.memory = 512 
        v.cpus = 1
    end
end

