# tomcat

# On AWS Create RHEL server

#Login

# Install Chef
$  curl https://omnitruck.chef.io/install.sh | sudo bash -s -- -P chefdk -c stable -v 2.0.28

# Install VIM
$ sudo yum install vim -y

# Add line to bottom of /etcsudoers
$ sudo vi /etc/sudoers

		abrendel        ALL=(ALL)       NOPASSWD: ALL



# Add local account
$ sudo useradd abrendel
$ sudo passwd abrendel
$ sudo su - abrendel
$ mkdir ~/chef_repo


# Install Git
$ sudo yum install git -y

# Setup the cookbooks and clone them from github
$ mkdir cookbooks
$ mkdir cookbooks/mongodb
$ mkdir cookbooks/tomcat
$ cd ~/chef_repo/cookbooks/mongodb ; git clone https://github.com/aaronbrendel/mongodb.git .
$ cd ~/chef_repo/cookbooks/tomcat ; git clone https://github.com/aaronbrendel/tomcat.git .



# Execute the Tomcat cookbook

# Like before, it should not work yet.
$ curl localhost:8080 

# I'm not sure I should say this….but lets cook up some tomcat
$ sudo chef-client --local-mode --runlist 'recipe[tomcat]'

# NOW IT WORKS!
$ curl localhost:8080



                                                                                                                                                                                          
