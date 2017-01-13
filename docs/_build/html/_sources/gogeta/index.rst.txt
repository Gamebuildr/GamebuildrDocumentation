
Gogeta SCM Microservice
======================================

Gogeta is the Gamebuildr microservice written in Go that montiors and clones code repositories. 
It currently supports Git and Github with other integrations in mind.

Currently Gogeta runs as a container on Kubernetes polling messages from Amazon SQS. When a new message is polled a new event is triggered 
and, based on the user profile (free, indie, enterprise), Gogeta will either pull the .zip archive or clone the full repo.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   gogeta-docker
   gogeta-kubernetes
