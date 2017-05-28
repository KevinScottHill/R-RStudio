# Install and configure a Shiny App on a red-hat linux instance

#### Follow instunctions layed out in [Install R and RStudio](https://github.com/KevinSHill/R-RStudio/blob/master/Install%20R%20and%20RStudio.md)

#### With R and RStudio Successfully Installed, Install the Shiny and RMarkdown Packages

```
sudo su - \
-c "R -e \"install.packages('shiny', repos='https://cran.rstudio.com/')\""

sudo su - \
-c "R -e \"install.packages('rmarkdown', repos='https://cran.rstudio.com/')\""
```

#### Get the shiny app files (find the latest files on [RStudio](https://www.rstudio.com/products/shiny/download-server/))
```
sudo su -
cd
wget https://download3.rstudio.org/centos5.9/x86_64/shiny-server-1.5.3.838-rh5-x86_64.rpm
```

#### Install Shiny Server
```
yum install --nogpgcheck shiny-server-1.5.3.838-rh5-x86_64.rpm
```

#### Make sure port 3838 is available through your firewall and use the IP_address(or DNS name):3838. You should see the shiny welcome screen

&nbsp;&nbsp;&nbsp;&nbsp;For more information visit RStudio [getting started guide for Shiny](http://docs.rstudio.com/shiny-server/#getting-started)



#### Open the configuration file
```
vim /etc/shiny-server/shiny-server.conf
```
Within the server block of code add:
```
,
location /myApp {
    app_dir /srv/shiny-server/myApp;
}
```
Save and close the file

#### Load your App to the server
create a new directory in the /srv/shiny-server directory
```
mkdir myApp
chmod -R 775 myApp
```
*FTP your file into the myApp location or copy and paste your code into a .R file*

#### In your browser navigate to --> IP_address(or DNS name):3838/myApp -- to use your new Shiny App!


