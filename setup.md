Node.js server setup
-----------------

digital ocean droplet | Ubuntu 14.04

````bash
# create new user
~# adduser <newuser>

# give new user root privileges
~# visudo
root    ALL=(ALL:ALL) ALL
(add)
<newuser>    ALL=(ALL:ALL) ALL

# configure ssh
~# nano /etc/ssh/sshd_config
Port <1025 - 65536>
Protocol 2
PermitRootLogin no
....
AllowUsers <newuser>

~# reload ssh

# ssh option if you've changed the port number
$ ssh -p <port number> <newuser>@<ip>
````

install nginx (latest version)
-----------------------------

````bash
$ sudo apt-get install python-software-properties
$ sudo apt-get install software-properties-common (was not needed)
$ sudo add-apt-repository ppa:nginx/stable
$ sudo apt-get update
$ sudo apt-get install nginx
# should start automatically; to check status:
$ service nginx status

nginx is installed in folder:
/etc/nginx

nginx config file:
/etc/nginx/nginx.conf

The default site is served from:
/usr/share/nginx/html

Default site config info:
/etc/nginx/sites-available/default
````

Install Node.js through nvm
-------------------------------
````bash
# add c++ compiler
$ sudo apt-get update
$ sudo apt-get install build-essential libssl-dev
$ curl https://raw.githubusercontent.com/creationix/nvm/v0.17.1/install.sh | bash
$ source ~/.profile

# list available Node.js versions
$ nvm ls-remote
$ nvm install <version>
$ nvm use <version>
$ node -v
$ nvm ls
$ nvm alias default <version>

# link 'node' to 'nodejs'
$ sudo ln -s "$(which nodejs)" /usr/bin/node

# subsequent: 
$ nvm use default
````

Grunt
-----------------------------
````bash
$ npm install -g grunt-cli
# installing dependencies
$ npm install grunt-contrib-concat <etc>
````

JSHint
---------------------------
````bash
$ npm install jshint -g
````

Git
-----------------------
````bash
# install
$ sudo apt-get update
$ sudo apt-get install git
$ git config --global user.name "<name>"
$ git config --global user.email "<email>"
$ git config --list
$ nano ~/.gitconfig

# using
$ mkdir git_testing
$ cd git_testing
$ touch file
$ git init
$ git add . [ or git add <file> ]
$ git commit -m "Some comment" -a [ or git commit -m "Some comment" <file> ]
# push to remote server
$ git remote add origin <repo path>
$ git push origin master
# subsequent push
$ git push
````

Yo / Bower / Grunt
-----------------
````bash
$ npm install -g yo
$ npm install -g generator-webapp
$ mkdir my-yo-project
$ cd my-yo-project
$ yo webapp
````

gdal / topojson
---------------
````bash
$ mkdir ~/downloads
$ cd ~/downloads
$ sudo apt-get install build-essential python-all-dev
$ wget http://download.osgeo.org/gdal/1.11.1/gdal-1.11.1.tar.gz
$ tar xvfz gdal-1.11.1.tar.gz
$ cd gdal-1.11.1
# configure with python bindings
$ ./configure --with-python
$ make
$ sudo make install
$ sudo ldconfig
````
