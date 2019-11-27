MUD Pi on Openshift
======

A simple text-based Multi-User Dungeon (MUD) game, which could be run on a 
Raspberry Pi or other low-end server.

This is a really simple fork from MUD Pi  written by Mark Frimston. This is to deploy it on Openshift. It's only for education or test purposes, not for playing at work... :p


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
