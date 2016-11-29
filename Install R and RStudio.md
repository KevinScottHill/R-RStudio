# Install R and R-Studio on a RedHat linux server

#### Begin by create the server on AWS or another location, set your firewalls, and SSH into the system.

#### Become the root:
    sudo su -

#### Create a new user (kevin) and password, this will be your R-studio login:
    useradd kevin
    passwd kevin

#### Install wget and vim packages:
    yum install vim wget -y

#### Download the latest EPEL release, find the most recent copy at https://fedoraproject.org/wiki/EPEL:
    su -c 'rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm'
    
#### Run a yum update:
    yum update -y
    
#### Change the redhat-rhui.repo file under"[rhui-REGION-rhel-server-optional]" make enable =1 for optional repos:
    cd /ete/yum.repos.d
    vim redhat-rhui.repo

#### Install R:
    yum install R -y
    
#### Get the rStudio file, the latest can be found at https://www.rstudio.com/products/rstudio/download-server/:
    cd
    wget https://download2.rstudio.org/rstudio-server-rhel-0.99.903-x86_64.rpm

#### Install rStudio
    yum install --nogpgcheck rstudio-server-rhel-0.99.903-x86_64.rpm
    
#### Make sure port 8787 is available through your firewall and use the IP_address(or DNS name):8787 and login using the username and password created
