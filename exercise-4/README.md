#   DEEP DIVING INTO LINUX

**Steps Followed In Solving The Exercise**

## 1:   Create The Three Group(*admin*, *support*, and *engeering*)
    Command: 
        groupadd admin (this group has already been created by default)
        groupadd support && groupadd engineering


## 2:   Add The Admin group To  *SUDOERs*
    Command: sudo visudo /etc/sudoers

        *   CHANGE  
                %admin ALL=(ALL) ALL 
        *   TO 
                %admin ALL=(ALL:ALL) ALL

    *   NB: The Recommended way of adding a USER or GROUP to SUDOERS is:

            *   sudo vi -f /etc/sudoers.d/username or groupname
            *   Now you are in the file, you can set any permission for a group or user. 
            for example:    %support ALL=(ALL) ALL (for support group)
                            user-in-a-group ALL=(ALL)  (for a user-in-a-group)

     
        


## 3:   *Create* and *Add* a *user* in each of the *groups*

    Command: sudo useradd -g groupname -m username


        ### NB: i didn't use the * useradd -aG admin,support,engineering username * to a user to all the groups in one shot because each group has to have a unique a user and because of the group permission (the admin-group is added to SUDOERs) 
        *       -g create a user with the initial login group
        *       -m create a user in the /home

## 4:   Generate SSH keys for user in the Admin-group. 
            * switch to the user-in-the-admin-group and ssh-keygen 
    
    Command:   sudo su - username-in-the-admin-group
                ssh-keygen



# THE OUTPUTS:

## CONTENT OF */etc/passwd*
![etc/passwd](/exercise-4/images/etc-passwd.PNG)


## CONTENT OF */etc/group*
![etc/group](/exercise-4/images/etc-group.PNG)


## CONTENT OF */etc/sudoers*
![etc/sudoers](/exercise-4/images/etc-sudoers.PNG)

