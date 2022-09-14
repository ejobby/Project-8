# Project-8

# Load Balancer Solution With Apache

The pre requisite configuration is the completing of Project 7 and making sure that all the webservers are connected to the db servers and also have there website hosted on the NFS Server. It must also be ensure that the Public IP address of all three Webservers can access the propitix Website on the browser.

## Configure Apache As A Load Balancer

Firstly spin up a Ubuntu Server Instance on AWS EC2 that will serve as the Apache Server used for Load Balancer and name it Project-8-apache

![Apache Server Instance](./Images/apache-launch.png)

Open Port 80 as an inbound rule under the Security group of the server instance

![HTTP Inbound Rule](./Images/inbound-port.png)

### Install Apache Load Balancer on Project-8-apache-lb server and configure it to point traffic coming to LB to both Web Servers

Copy the code below line by line to install the apache on the server 

```
sudo apt update
sudo apt install apache2 -y
sudo apt-get install libxml2-dev
```

Then enable some modules by coping the code underneath line by line and run the code

```
sudo a2enmod rewrite
sudo a2enmod proxy
sudo a2enmod proxy_balancer
sudo a2enmod proxy_http
sudo a2enmod headers
sudo a2enmod lbmethod_bytraffic
```

Restart apache2 service

`sudo systemctl restart apache2`

`sudo systemctl status apache2`

![Apache Status](./Images/apache-status.png)

