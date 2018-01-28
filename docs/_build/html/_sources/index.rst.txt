.. Gamebuildr documentation master file, created by
   sphinx-quickstart on Tue Dec 20 14:24:44 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Gamebuildr Documentation
======================================

**Welcome to the Gamebuildr dev docs!** This website holds documentation about our dashboard application and information about the microservices used to power our CI/CD solutions. 

Currently our main services are:

* The web app which is our main visial dashboard.
  * React/Redux
  * es6

* The web api 
  * node.js
  * es6

* Hal: Container API service to start up and close down microservice
  * golang

* Dave: Docker container custom management system
  * golang

* Gogeta: Source control monitor and updater
  * golang

* Mr. Robot: Game engine builder
  * golang

Everything on this website is related to our architecture and how everything works together.

Navigation
------------

.. toctree::
   :maxdepth: 2
   :caption: Microservices:

   gamebuildr/index
   gogeta/index
