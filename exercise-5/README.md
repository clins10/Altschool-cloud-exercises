# INSTALLING PHP7.4 ON UBUNTU 20.04 USING ppa:ondrej/php

## STEPS:

### 1:  Add some dependencies which are not compulsory but very import
    
    Command:    sudo apt install software-properties-common apt-transport-https -y

### 2:  Add ppa:onderej/php repository

    Command:    sudo add-apt-repository ppa:ondrej/php -y

### 3:  Run update to make the repository recognizable by linux package manager **A Must STEP**

    Command:    sudo apt update

    *   Also run an upgrade make the repo up to date
        Command:    sudo apt upgrade -y

### 4:  Now we are ready to install PHP7.4

    Command:    sudo apt install -y php7.4 php7.4-common


### CONTENT OF **/etc/apt/sources.list**

![/etc/apt/sources.list](/exercise-5/images/sources-list.PNG)


### CONTENT OF **php -v**

![php -v](/exercise-5/images/php-v.PNG)


