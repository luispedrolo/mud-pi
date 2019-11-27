MUD Pi om Openshift
======

A simple text-based Multi-User Dungeon (MUD) game, which could be run on a 
Raspberry Pi or other low-end server.

This is a really simple fork from MUD Pi  written by Mark Frimston. This is to deploy it on Openshift. It's only for education or test purposes, not for playing at work... :p


Requirements
------------

You will need to install _Python_ (2.7+ or 3.3+) where you wish to run the 
server. Installers for Windows and Mac can be found at 
<http://www.python.org/download/>. There are also tarballs for Linux, although 
the best way to install on Linux would be via the package manager.

To allow players to connect remotely, the server will also need to be connected
to the internet. 

To connect to the server you will need a telnet client. On Mac, Linux, and 
versions of Windows prior to Windows Vista, the telnet client is usually 
installed by default. For Windows Vista, 7, 8 or later, you may need to follow
[this guide](http://technet.microsoft.com/en-us/library/cc771275%28v=ws.10%29.aspx)
to install it.


Deploying it on Openshift
------------------

	oc new-app python:3.6~https://github.com/luispedrolo/mud-pi.git --name test
	oc edit svc test
	
By editing the service you have to expose the port 1234

Connecting to the Server
------------------------
On a node:



	telnet test.my_project.svc 1234
	
	
	
where `my_project` is the name of the project (namespace) where you've deployed this app.

If you want to connect from another node you have to create a route by exposing the service or editing the service to change it to NodePort.

Make sure the telnet is installed. On the contrary on CentOs or Red Hat use yum install telnet -y




Author
------

MUD Pi was written by Mark Frimston

For feedback, please email <mfrimston@gmail.com> or add a comment on the 
project's [Github page](http://github.com/frimkron/mud-pi)
