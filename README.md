[![Build Status](https://travis-ci.org/ahelal/ansible-portforward.svg?branch=master)](https://travis-ci.org/ahelal/ansible-portforward)
ansible-portforward
===================

This ansible role deploys portfoward script that controls iptables for Ubuntu 12.04 (tested on vagrant)


##Prerequisite
* Having ansible installed on your workstation. 


##How to install
* Use github to clone/fork in your role directory
* ansible galaxy ```ansible-galaxy install adham.helal.portforward```

##Variables 
  All the default variables are located **defaults/main.yml**. Mostly you would need to configure the following variables. 
  - *PFRules:* You can define one or more portfoward rules 
 
      ```
     PFRules:
      - Type: m
        Interface: eth0
        LocalPort: 2222
        DestPort : 22
        DestIP   : 12
        Comment  : "eth0:2222->127.0.0.1:22"

      - Type: n
        Interface: eth0
        LocalPort: 8080
        DestPort : 80
        DestIP   : 127.0.0.1
        Comment  : "eth0:8080->127.0.0.1:80" 
      ```
    
     ```Type:``` Either "n" for nat or "m" for masquerade
     
     ```Interface:``` network interface 
     
     ```LocalPort:``` Local Port
     
     ```DestPort:```Destination port
     
     ```DestIP:```  Destination IP
     
     ```Comment:``` Comments
     

##Configure
You can configure your variables in ansible with one of the following

 * Create a variable in host/group variables directory. (recommended)
 * Editing var/main.yml
 * Run ansible-playbook with -e
 * Edit the default/main.yml (not recommended)

##Run
**By default nothing will happen if you deploy witout configuration**
    
  ```ansible-playbook -l hostname portforward.yml```

 
