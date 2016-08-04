# Easy Install Firewall


This project will help to install a firewall on Linux with the help of [Firewall Builder](http://www.fwbuilder.org/) to create the firewall script.


## Requirements


* SystemD

* IPTables

* Firewall Builder

* Sudo permission

## Configuration

You have the option to configure the firewall script with [Firewall Builder](http://www.fwbuilder.org/) through this launcher, but
you can do it manually by double-clicking the file *'src/firewall.fwb'*.
Remember if! After setting, save and compile.

The project *'src/firewall.fwb'* has two types of firewall, utm for dynamic IP and one for static IP.
Set up according to what you use. 

## Installation

* 1 - Install Firewall Builder according to your Linux distribution.

* 2 - Do the clone project and enter the folder

~~~shell
shell> git clone https://github.com/williamcanin/firewall-linux.git && cd firewall-linux
~~~


* 3 - Run the command:

~~~shell
shell> ./init -i
~~~

* 4 - This installation launcher will follow you to the end.