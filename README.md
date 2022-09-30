# Altschool-Cloud-Engineering-exercises
    Documenting my cloud engineering journey at Altschool Africa

## Table of Contents

## [Exercise 1](/exercise-1)
   **TASK:** 
    *Setup Ubuntu 20.04 on your local machine using Vagrant

   **INSTRUCTION:**

    *Customize your Vagrantfile as necessary with private_network   set to #dhcp
    ..* Once the machine is up, run #ifconfig and share the output in your submission along with your Vagrantfile in a #folder for this exercise.

## [Exercise 2](/exercise-2)
    **__TASK:
        *Research online for 10 more linux commands aside the ones already mentioned in this module.
        *Submit using your altschool-cloud-exercises project, explaining what each command is used for with examples of how to use use each and example screenshots of using each of them.
       
    **__INSTRUCTION:
        *Submit your work in a folder for this exercise in your altschool-cloud-exercises project. You will need to learn how to embed images in the markdown files. 


## [Exercise 3](/exercise-3)
    **__TASK:
        *Create 3 groups - Admin, Support & Engineering and  add the admin group to #sudoers.
        *Create a user in each of the groups.
        *Generate #SSH keys for the user in the admin group.
    
    **__INSTRUCTION:
        *Submit the content of #etc/passwd, #etc/group and #etc/sudoers.


## [Exercise 4](/exercise-4)
    **__TASK:
        *Install #PHP7.4 on your local linux machine using the #ppa:ondre/php package repo.
    
    **__INSTRUCTION:
        *Learn how to use the add-apt-repository command
        *Submit the content of #etc/apt/sources.list and the output of #php -v command.


## [Exercise 5](/exercise-5)
    **__TASK:
        *You already have a Github account, also setup a GitLab account if you you don't have one already.
        *You already have a altschool-cloud-exercises project, clone the project to your local system.
        *Setup your name and email in Gut's config.

    **__INSTRUCTION:
        *Submit the output.
        *git config -l
        *git remote -v
        *git log


## [Exercise 6](/exercise-6)
    **__TASK:
        *Review the CIS benchmark for ubuntu, and try to implement at least 10 of the recommendations that we made within the benchmark.

    **__INSTRUCTION:
        *N/A


## [Exercise 7](/exercise-7)
    **__TASK:
        *Create a bash script to run at every hour, saving system memory (RAM) usage to a specified file and at midnight it sends the content of the file to a specified email address, then starts over for the new day.
    
    **__INSTRUCTION:
        *Submit the content of your #script, #cronjob, and a sample of the email sent, all in the folder for this exercise.


## [Exercise 8](/exercise-8)
    **__TASK:
        *Create a Ansible Playbook to setup a server with Apache.
        *The server should be set to #Africa/Lagos Timezone.
        *Host an index.php file with the following content, as the main file on the server:
            <?php
                date (" F d, Y h:i:s A e", time());
            ?> 
    
    **__INSTRUCTION:
        *Submit the #Ansible playbook, #the output of the systemctl status apache2 after deploying the playbook, a screenshot of the rendered page.


## [Exercise 9](/exercise-9)
    **__TASK:
        #193.16.20.35/29

             +B WHAT IS; 
            *Network IP?
            *Number of Hosts?
            *Range of IP addresses?
            *Broadcast IP from the this subnet? 
    
    **__INSTRUCTION:
        * Submit all your answers as a markdown file in the for this exercise.
