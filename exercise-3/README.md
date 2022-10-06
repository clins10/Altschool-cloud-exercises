#   DEEP DIVING INTO LINUX

**Steps Followed In Solving The Exercise**

## 1:   Create The Three Group(*admin*, *support*, and *engeering*)
    Command: 
        groupadd admin
        groupadd support
        groupadd engineering


## 2:   Add The Admin group To  *SUDOERs*
    Command: %admin ALL : (ALL) ALL 
        


## 3:   Add a *user* in each of the *groups*
    Command: useradd -a -G <username> <groupname>


        #### NB: i didn't use the * useradd -a -G Admin,Support,Engineering * to a user to all the groups in shot because each group has to have a unique a user and because of group privileges(the Admin-group is added to SUDOERs) 

## 4:   Generate SSH keys for user in the Admin-group. 
            * cd into the Admin group directory and ssh-keygen 
    
    Commmand: ssh-keygen




# THE OUTPUTS:

##CONTENT OF */etc/passwd*
![etc/passwd]()


##CONTENT OF */etc/group*
![etc/group]()


##CONTENT OF */etc/sudoers*
![etc/sudoers]()

