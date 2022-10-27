# ALTSCHOOL AFRICA MINI PROJECT

## INSTRUCTIONS:




**I  Carried Out This Mini Project  Using *AWS as my Cloud Provider* and *NameCheap for my Domain Name* (viatech.me)**



## STEP 1:

## SETTING UP EC2 INSTANCE ON AWS

    1.1 Login to your AWS account, search for EC2 service and click on it.
    1.2 Click on Launch Instance
    1.3 Enter a name for your instance a name, under the Name and tags section
    1.4 Select the operating system you want to use for your instance (since we are using   debian 11, i select debian 11 AMI)
    1.5 Select the instance type (i select t2.micro since it is free tier eligible)
    1.6 Select key pair:
        1.6.1 click on create a new key pair
        1.6.2 enter a name for your key pair
        1.6.3 select pair type as RSA
        1.6.4 select private key file type as .pem
        1.6.5 click on create key pair
        **NOTE: the key will be downloaded to your local machine, keep it safe **
           
    1.7 Create a new security group that allows SSH, HTTP and HTTPS traffic
    1.8 Configure the storage (i selected 8GiB gp2 for the root volume)
    1.9 Click on launch instance:
        **Next Steps**
        1.9.1 Create a billing and free tier usage alerts and fill in your email address
        1.9.2 Click on connect to your instance:
            1.9.2.0 Click on the SSH client tab
            1.9.2.1 Copy the command(containing the instance public DNS) with the key pair file name. #NOTE: the key pair file name is the name you gave your key pair when you created it

## CREATING AN ELASTIC IP ADDRESS AND POINTING IT TO OUR DOMAIN NAME

    *.1 Click network and security on the left side of the dashboard
    *.2 Click on Elastic IP address
    *.3 Click on Allocate Elastic IP address
    *.4 Click on Actions
    *.5 Click on Associate Elastic IP address
    *.6 Select the instance you want to associate the elastic IP address to
    *.7 Click on Associate

## STEP 2:
    **NB: it's adviced to have a registered domain before taking this step**

##  REGISTERING YOUR DOMAIN ON AWS

    2.1 Login to your AWS account, search for Route 53 service and click on it.
    2.2 Click on create hosted zone, under DNS management:
        2.2.1 Domian name: Enter your domain name in the domain name field (i used viatech.me)
        2.2.2 Description is optional- but you can enter a description to help distinguish your hosted zone from others
        2.2.2 Select public hosted zone
        2.2.3 Click on create hosted zone

    2.3 Enter your domain name (i used viatech.me)
    2.4 Select public hosted zone
    2.5 Click on create hosted zone
    2.6 Click on create record:
        2.6.1 choose quick create record- since we just hosting a demo project
        2.6.2 Record name: keep blank to create a record for the root domain (i.e viatech.me)
        2.6.3 Record type: Select A - IPv4 address
        2.6.4 Value: Enter the elastic IP address you created for your EC2 instance
        2.6.5 TTL: keep default- 300 seconds (5 minutes) - recommended value is 60 - 172800 secs (48 hours)
        2.6.6 Click on create record
    **NOTE: i created another record for a subdomain (i.e www.viatech.me and server.viatech.me)**
    **NOTE: you can create as many records as you want for your domain**

## SETTING UP A DOMAIN NAME ON NAMECHEAP

    2.1 Login to your NameCheap account, click on the Domain List tab and click on Manage
    2.2 Scroll down to the NAMESERVERS section and locate the Custom DNS section
    2.3 Click on ADD NAMESERVERS:
        2.3.1 go back to your AWS account, locate the hosted zone you created for your domain and click on it. locate the NS row (the row with four entries) and copy the values.
        2.3.2 paste the values in the custom DNS section of your NameCheap account
        2.3.3 click on save.

## STEP 3:

## CONNECTING TO YOUR EC2 INSTANCE USING SSH

    3.1 Open your terminal
    3.2 Navigate to the directory where you saved your key pair file
    3.3 Run the command you copied from the AWS console
    3.4 Enter yes when prompted
    3.5 You are now connected to your EC2 instance

## STEP 4:

## LET'S SETUP OUR SERVER NAME, HOSTNAME, AND TIMEZONE

### 4.1  Run the following command to set up your server name:

```bash
sudo hostnamectl set-hostname server.viatech.me --static
```
```bash
sudo hostnamectl set-hostname server.viatech.me --transient
```
```bash
sudo hostnamectl set-hostname "Viashima's Server" --pretty
```

### 4.2 Run the following command to set up your timezone:
```bash
sudo timedatectl set-timezone Africa/Lagos
```
```bash
sudo timedatectl set-ntp true
```

### 4.3 Run the following command to set up your hostname:
```bash
sudo vi /etc/hosts
```
**NOTE: add the following line to the file**
     127.0.1.1 server.viatech.me server     # replace server.viatech.me with your hostname
     18.168.174.68 server.viatech.me        # this is the elastic IP address of my EC2 instance

   Hit the escape key, SHFT+ZZ to save and exit the file #NOTE: you can also use :wq to save and exit the file


## STEP 4:

## INSTALLING LAMP WITH OTHER PACKAGES AND NECESSARY DEPENDENCIES NEEDED TO DEPLOY LARAVEL ON DEBIAN 11 OS

### 4.1 Run the following commands to update and upgrade your system
```bash
sudo apt update && sudo apt upgrade -y
```

### 4.2 Lets install some useful packages:
    ```bash
sudo apt install -y curl wget ufw unzip
```

#####   *curl* is used to download files from the internet and provides the libcurl library.
#####   *wget* is just a simple command line also used to download files from the internet.
#####   *ufw* is used to configure the firewall.
#####   *unzip* is used to unzip files

### 4.3 INSTALLING APACHE2 WEB SERVER

####    Run the following commands to install *apache2* and all the required dependencies
```bash
sudo apt install -y apache2
```
    
####    Run the following commands to enable apache2
```bash
sudo systemctl enable apache2
```

## 4.4 SETTING UP THE FIREWALL

### 4.4.1 Run the following commands to set up the firewall
```bash
sudo ufw allow OpenSSH
```
```bash
sudo ufw allow http
```
```bash
sudo ufw allow https
```
```bash
sudo ufw enable
```

### 4.4.2 Run the following commands to check the status of the firewall
```bash
sudo ufw status
```

### 4.4.3 Run the following commands to check the status of apache2
```bash
sudo systemctl status apache2
```


## 4.5 INSTALLING PHP

### 4.5.1 Run the following commands:
```bash
sudo apt update -y
```
```bash
sudo apt install apt-transport-https lsb-release ca-certificates -y
```
```bash
sudo apt install apt-transport-https gnupg2 -y
```
#### Thecommand installs: apt-transport-https, gnupg2, and ca-certificates. All 3 packages are tools that help ensure you are connecting to the actual repo, not a MITM. In other words, they ensure secure access to the php repo.

### 4.5.2 Run the following commands:
```bash
echo "deb https://packages.sury.org/php/ $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/sury-php.list
```

#### This command basically adds the *Sury php repo* for lsb_release to our machine’s apt sources list.

### To know the short codename for the Linux distro you are using Run:
```bash
lsb_release -cs
```

### 4.5.3 Run the following commands:
```bash
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
```
```bash
sudo apt update -y
```

#### This downloads the gpg key for php and stores them in the /etc/apt/trusted.gpg.d/php.gpg file. The gpg key is a resource of the gnupg2 we installed earlier. It basically ensures that you are getting the php package from an authentic source.

### 4.5.4 Run the following commands:
```bash
sudo apt install php8.1 php8.1-curl libapache2-mod-php php8.1-dev php8.1-bcmath php8.1-zip php8.1-mbstring php-json php8.1-mysql php8.1-gd php8.1-xml php8.1-tokenizer php-common
```

####    Run this command if the first didn't work
```bash
sudo apt-get install php8.1 libapache2-mod-php php8.1-dev php8.1-zip php8.1-curl php8.1-mbstring php8.1-mysql php8.1-gd php8.1-xml
```

#### This command installs PHP 8.1, Apache2 php module, PHP curl, PHP MySQL, and various other PHP extensions.

### Run the following commands to check the version of PHP installed
```bash
php -v
```
### OR
```bash
php --version
```

## 4.6 INSTALLING COMPOSER

### CD to your root directory
```bash
cd ~ 
```
```bash
sudo su -
```

### 4.6.1 Run the following commands:
```bash
sudo curl -sS https://getcomposer.org/installer | php
```

#### This command downloads the composer installer and pipes it to the php command. The php command then executes the installer.


### Run the following commands to move the composer.phar file to the /usr/local/bin directory
```bash
sudo mv composer.phar /usr/local/bin/composer
```

### Run the following command to make the composer.phar file executable
```bash
sudo chmod +x /usr/local/bin/composer
```

### Run the following command to check the version of composer installed
```bash
composer --version
```
**NOTE: if you get an error, run the following command**
```bash
sudo apt install php8.1-cli
```
```bash
composer --version
```
### CD back to your home directory
```bash
cd ~
```

## 4.7 INSTALLING MYSQL

### 4.7.1 Add the latest mysql repository to your system
```bash
wget -c https://dev.mysql.com/get/mysql-apt-config_0.8.24-1_all.deb
```

#### This command downloads the latest MySQL apt configuration package to your present working directory    (at the time of writing this, the latest version was 0.8.24–1). 
    The -c option ensures that the download is resumed if it was interrupted.

### 4.7.2 Run the following commands:
```bash
sudo dpkg -i mysql-apt-config_0.8.24-1_all.deb
```

#### This command installs the downloaded package. The dpkg command is used to install, remove, and manage Debian packages.

####    Run the following command if the dkpg command didn't work
```bash
sudo apt install ./mysql-apt-config_0.8.24-1_all.deb
```

**NB: You will be prompted to select the MySQL version you want to install. Select the latest version and press Enter.**

### 4.7.3 Now let's install MySQL
```bash
sudo apt update -y
```
```bash
sudo apt install mysql-server -y
```
**NB: You will be prompted to enter a password for the MySQL root user. Enter a strong password and press Enter.**

### Run the following commands to check the status of MySQL
```bash
sudo systemctl status mysql
```

### 4.7.4 Run the following commands to secure your MySQL installation
```bash
sudo mysql_secure_installation
```
**NOTE: You will be prompted to enter the current password for the root user. and other security questions**

### Run the following commands to check the version of MySQL installed
```bash
mysql --version
```

### 4.7.5 Create a database for your Laravel application
```bash
mysql -u root -p
```
```bash
CREATE DATABASE miniproject_db;
```
```bash
USE miniproject_db;
```
### this will create a database named miniproject_db, and enable it to be used.

**Now we need to pull the laravel app from github so we can use it**

## 4.8 INSTALLING GIT
### 4.8.1 Run the following commands:
```bash
sudo apt update -y
```
```bash
sudo apt install git -y
```
### Run the following commands to check the version of git installed
```bash
git --version
```

### 4.8.2 Run the following commands to set up your git credentials
    *git config --global user.name "Your Name"*
    *git config --global user.email "Your Email"*
     Example:
```bash
git config --global user.name "Viashima"
```
```bash
git config --global user.email "vnongu@gmail.com"
```
    

### 4.8.3 Run the following commands to clone the laravel app project from github
```bash
sudo git clone https://github.com/f1amy/laravel-realworld-example-app.git
```
```bash
sudo mv laravel-realworld-example-app mylaravel-app
```

### This will clone the laravel app from github and move it to a folder named mylaravel-app

### 4.8.4 Run the following commands to install the laravel app dependencies
```bash
cd mylaravel-app
```
```bash
composer install
```
```bash
cd ~
```

### 4.8.5 Run the following commands:
```bash
sudo cp mylaravel-app /var/www/html
```
```bash
cd /var/www/html/mylaravel-app
```
```bash
sudo chown -R www-data:www-data /var/www/html/mylaravel-app
```
```bash
sudo chmod -R 755 /var/www/html/mylaravel-app
```

### This will copy the laravel app to the /var/www/html directory, change the owner of the laravel app to www-data and change the permissions of the laravel app to 755.

### Run the following commands:
```bash
sudo cp .env.example .env
```
```bash
sudo vi .env
```
**edit the .env file and change the following lines to match your credentials-datacase and IP address**
    APP_NAME="mylaravel-app"
    APP_ENV=local
    APP_KEY=
    APP_DEBUG=true
    APP_URL=http://18.168.175.68 #change this to your server IP address
    APP_PORT=3000

    LOG_CHANNEL=stack
    LOG_DEPRECATIONS_CHANNEL=null
    LOG_LEVEL=debug

    DB_CONNECTION=mysql
    DB_HOST=127.0.01
    DB_PORT=3306
    DB_DATABASE=miniproject_db
    DB_USERNAME=root
    DB_PASSWORD= miniproject_password

    BROADCAST_DRIVER=log
    CACHE_DRIVER=file
    
**save and exit the .env file**

### Run the following commands:
```bash
sudo php artisan key:generate
```
```bash
sudo php artisan migrate
```

### This will generate the application key and run the database migrations.
    
###Run the following commands:
```bash
cd routes
```
```bash
sudo vi web.php
```
**edit the web.php file to look exactly like this**
    Route::get('/', function () {
    return view('welcome');
    });
### this will change the default laravel page to the welcome page
**save and exit the web.php file**

### Run the following commands to edit the apache2 configuration file
```bash
cd /etc/apache2/sites-available
```
```bash
sudo vi mylaravel-app.conf
```
**edit the mylaravel-app.conf file to match your credentials**

    <VirtualHost *:80>
        ServerName server.viatech.me            #change this to your server IP address
        ServerAdmin service@server.viatech.me    #change this to your email address
        DocumentRoot /var/www/html/mylaravel-app/public

        <Directory /var/www/html/mylaravel-app/>
                AllowOverride All
                Require all granted
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
    
**save and exit the mylaravel-app.conf file**

### This above commands will create a virtual host for your laravel app

### Run the following commands:
```bash
sudo a2ensite mylaravel-app.conf
```
```bash
sudo a2dissite 000-default.conf
```
```bash
sudo systemctl restart apache2
```

### this commands will disable the default apache2 virtual host and enable the mylaravel-app virtual host

## if everything went well, you should be able to access your laravel app from your browser using your domain name or IP address

## The laravel app should look like this:

![laravel app](/mini-project/images/final-output.PNG)







