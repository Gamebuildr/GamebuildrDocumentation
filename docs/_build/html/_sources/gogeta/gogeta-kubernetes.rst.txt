Gogeta Kubernetes
=================

Gogeta's docker containers run across multiple Kubernetes clusters to spin up a new cluster create a Google Kubernetes cluster 
through either the dashboard on in the provided console.

Push to a cluster
*****************

Note: This assumes you're using your local command prompt.

To push to a cluster you first need to build your docker image tag it appropriately, and push to googles container engine:

.. code-block:: bash

    docker build -t gamebuildr/gogeta
    docker tag gamebuildr/gogeta gcr.io/:projectname/gogeta
    gcloud docker -- push gcr.io/:projectname/gogeta

After tagging and pushing you should prep your local environment to enable pushing to your cluster:

.. code-block:: bash

    gcloud config set project :projectname
    gcloud config set compute/zone :region
    gcloud config set container/cluster :clustername
    gcloud config set container/use_client_certificate true
    gcloud container clusters get-credentials :clustername
    kubectl run :clustername --image=gcr.io/:projectname/gogeta --port=8080

You'll now be able to see your docker image running on your new cluster!