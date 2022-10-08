# CONNECTING FROM ONE MACHINE TO ANOTHER USING SSH (VAGRANT)

## STEPS:

1.  Enter into your vagrantfile and set-up your machines (herein master and servant)

        Command: vi vagrantfile
        
        *   config.vm.define "master" do |subconfig|
                subconfig.vm.box = "ubuntu/focal64"
                subconfig.vm.hostname = "master"
                subconfig.vm.network "private_network", type: "dhcp"

            end

        *   config.vm.define "servant" do |subconfig|
                subconfig.vm.box = "ubuntu/focal64"
                subconfig.vm.hostname = "servant"
                subconfig.vm.network "private_network", type: "dhcp"
            end

        *   # Run an inline script to install avahi-daemon and libnss-mdns while the machine is being provisioned.

                config.vm.provision "shell", inline: <<-SHELL
                        sudo apt-get update
                        sudo apt-get install -y avahi-daemon libnss-mdns
                SHELL


2.  Spin up your vagrant machine
  
        Command: vagrant up  


3.  SSH into your servant machine and enable some permission **PasswordAuthentication yes** and  
    **PubkeyAuthentication yes** to allow connection from the master machine.
    
            Command: vagrant ssh servant
            Command: sudo vi /etc/ssh/sshd_config       # Enable the above mentioned permissions
            Command: sudo service sshd restart          # To effect the changes made in the sshd_config file
            Command: ifconfig                          # To get the ip address of the servant machine

    *   copy the ip address of the servant machine and keep somewhere you will need it later.
    *   exit the servant machine


4.  SSH into your master machine and generate an *ssh-key* for the master machine and copy it 
    to the servant machine.
    
            Command: vagrant ssh master
            Command: ssh-keygen
            Command: ssh-copy-id -i ~/.ssh/id_rsa.pub vagrant@ip-address-of-servant-machine
    *   NB: you can also use the command **ifconfig** to get the ip address of the master machine.

    
5.  SSH into your servant machine and check the **/home/vagrant/.ssh/authorized_keys** file to see if the
    master machine's ssh-key is there.
    
            Command: vagrant ssh servant
            Command: cat /home/vagrant/.ssh/authorized_keys
    *   exit the servant machine


6.  SSH into your master machine and check if you can connect to the servant machine without
    being prompted for a password.
    
            Command: vagrant ssh master
            Command: ssh vagrant@ip-address-of-servant-machine
    *   exit the master machine



## THE SCRIPT
![script](/exercise-3/images/the-script.PNG)



## OUTPUT OF THE ABOVE STEPS:

![output](/exercise-3/images/master-servantt-log-screenshot.PNG)


  

  
