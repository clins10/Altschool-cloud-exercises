# Connecting Github Account with Gitlab Account, cloning the Altschool-cloud-exercises to local machine, and Setting-Up Name and Email in the Git global config.

# STEPS:    
# 1.  Connecting Github account with Gitlab account:
    1.1  Go to *Gitlab* and click on *Settings*.

    1.2  Click on *Account*.

    1.3  Click on *Linked Accounts*.

    1.4  Click on *Github*.

    1.5  Click on *Connect*.

    1.6  Enter *Github* username and password.

    1.7  Click on *Sign in*.

    1.8  Click on *Authorize Gitlab*.

    1.9  Click on *Close window*.


# 2.  Cloning the Altschool-cloud-exercises to local machine:

    2.1  Go to *Gitlab* and click on *Projects*.

    2.2  Click on *altschool-cloud-exercises*.

    2.3  Click on *Clone*.

    2.4  Copy the *SSH* link.

    2.5  Open *Git Bash*.

    2.6  Change the current working directory to the location where you want the cloned directory to be made.

    2.7  Type *git clone*, and then paste the URL you copied in Step 2.4.

        2.7.0 $ git clone
    2.8  Press *Enter* to create your local clone.


# 3.  Setting-Up Name and Email in the Git global config:
    
        3.1  Open *Git Bash*.
    
        3.2  Change the current working directory to the location where you want the cloned directory to be made.
    
        3.3  Type *git config --global user.name "Your Name"*
    
            3.3.0 $ git config --global user.name "Your Name"
        3.4  Type *git config --global user.email "Your Email"*
    
            3.4.0 $ git config --global user.email "Your Email"
        
    
# OUTPUT OF *git config -l*
![git config -l](/exercise-6/images/config_-l.PNG)

# OUTPUT OF *git remote -v*
![git remote -v](/exercise-6/images/git_remte_-v.PNG)

# OUTPUT OF *git log*
![git log](/exercise-6/images/git-log.PNG)



    