Open5GS on Kubernetes
=====================

Scripts to build and deploy [Open5GS](https://open5gs.org/) on Kubernetes.

*Work in progress*


Instructions
------------

### Step 1: Build

The build scripts assume you are running on Fedora. If you don't have access to a baremetal Fedora
machine you can use our [Vagrant](https://www.vagrantup.com/) configuration that will set up a virtual
machine for you. To use it, change into this repository's directory and run:

    vagrant up
    vagrant ssh
    cd /vagrant

1. install-build-dependencies
2. build-binaries
3. build-container-image

### Step 2: Deploy

You will need access to a Kubernetes cluster. For testing you can use
[Minikube](https://minikube.sigs.k8s.io/).

1. deploy-mongodb
2. deploy-certificates
3. generate-configs
4. deploy-configs
5. publish-container-image
6. deploy-open5gs

### Utilities

You can see the logs of any component:

    ./log mme

And also get a shell to a container for debugging:

    ./shell mme


TODO
----

* Restart components when configmaps are updated
* Make use of [Reposure](https://reposure.puccini.cloud/) optional
