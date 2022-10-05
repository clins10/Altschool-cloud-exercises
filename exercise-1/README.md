# SETTING UP LINUX OS ON A WINDOWS SYSTEM
  **STEPS:**

    * download Oracle Virtual Machine virtualbox from https://www.virtualbox.org/wiki/Downloads

    * follow the procedures and install it on your system.
        * please do not try installing the linux os manually by using the VM- vagrant will help us to that *
      * Now let's create a hierarchy of folders or directories to house our vagrant boxes.

    * Create a folder either on your desktop or any location on your system but preferably in you c:/ drive to avoid windows naming issues. for ease of identification let's follow this sequence vagrant/boxes/ubuntu20.04-LTS that is vagrant-folder fathers boxes-folder that fathers ubuntu20.04-LTS.

    * Next go to your terminal either powershell, bash or command prompt and cd into ubuntu20.04-LTS
    * In your terminal enter the command "vagrant init ubuntu/focal64" to install vagrant 
    * vagrant up
    * vim  vagrantfile or vi vagrantfile or nano vagrantfile. enter the file and change your network configuration to " dhcp" exit the text editor
    * "vagrant ssh" to enter into the vagrant 
    * "sudo apt update" then "sudo apt install net-tools"
    * "ifconfig"

  ###   "ifconfig" Output 
  ![terminal screenshot of "ifconfig"](/exercise-1/images/ifconfig.PNG)

  ###   Vagrantfile Output 
  ![terminal screenshot of "vagrantfile"](/exercise-1/images/vagrantfile.PNG)