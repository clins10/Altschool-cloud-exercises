# Ascript that saves Ram memory usage to a file and sends it to an email address at midnight every day.

# Procedure:

## 1. setup SSMTP to send email
    > here we will use mailtrap as our email service provider
    > go to https://mailtrap.io/ and create an account
    > create a new inbox and copy the SMTP settings to the ssmtp.conf file
    1.1. ## install ssmtp and mailutils
        > sudo apt-get install ssmtp -y && sudo apt-get install mailutils -y
        1.1.1 ## edit the ssmtp.conf file
            > sudo vi /etc/ssmtp/ssmtp.conf
            root=enter_any_mail_address_since_we_are_using_mailtrap
            mailhub=smtp.mailtrap.io:2525 NB: the port number could be any of the four ports provided by mailtrap
            FromLineOverride=YES NB: this is to override the default mail address
            hostname=your_hostname NB: you can get your hostname by running the command hostname(ensure to set the hostname by running the command sudo hostnamectl set-hostname your_hostname)
            > ## copy and paste
            AuthUser=your_mailtrap_username
            AuthPass=your_mailtrap_password
            UseSTARTTLS=YES
            UseTLS=Optional

    > NB: you can also use gmail as your email service provider
    > go to https://myaccount.google.com/lesssecureapps and enable less secure apps to allow ssmtp to send email from your gmail account


## 2. create a bash script to save ram memory usage to a file and send it to an email address at midnight every day
    2.1 ## create a directory(called logs) and cd into it and create file called ram_logs.sh and make it executable
        > mkdir logs && cd logs
        > sudo vi ram_logs.sh
        > sudo chmod +x ram_logs.sh
    > copy and paste the following code into the ram_logs.sh file
        #!/usr/bin/bash NB: To know your file path type **which bash** in the terminal
        # create variables
        LOGFILE=/home/vagrant/logs/ram.log # to save the ram memory usage to a file
        SENDTIME=$(date +%H:%M) # to get the current time
        SENDTO=your_email_address # to send the ram memory usage to an email address
        
        # create a function called createLog # to create a log file
        function createlog() {
            if test -f $LOGFILE; then
                rm -rf &LOGFILE
                
            else
                touch $LOGFILE          # create a log file
                date >> $LOGFILE        # to get the current date
                free -h >> $LOGFILE     # to get the ram memory usage
            fi
        }

        # send the content of the file to an email address at midnight every day
        if [[ $SENDTIME -eq 0000 ]]; then
            createlog # call the createLog function
            echo "enter_the_body_of_you_email_here" | mail -s "enter_email_subject" -A $LOGFILE $SENDTO
        fi
        

    > NB: you can change the time to any time you want
    > NB: you can change the email address to any email address you want
    > NB: you can change the file name to any name you want


## 3. create a cronjob to run the script at midnight every day
    > sudo crontab -e
    > copy and paste the following code into the crontab file
        0 0 * * * bash /home/vagrant/logs/ram_logs.sh NB: this will run the script at midnight every day

        > NB: you can change the time to any time you want
        > NB: you can change the file path to any path you want


## 4. check your email to see the ram memory usage
    > NB: you can check your email at https://mailtrap.io/inboxes/your_inbox_id/messages
    

# SCREENSHOT OF *script*, *cronjob* and *sample of email sent*

## script
![script](/exercise-8/images/bash-script.PNG)

## cronjob
![cronjob](/exercise-8/images/cronjob.PNG)

## sample of email sent
![email-sample-sent](/exercise-8/images/)