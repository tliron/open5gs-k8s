Open5GS on Kubernetes
=====================

Scripts to build and deploy [Open5GS](https://open5gs.org/) on Kubernetes.

*Work in progress*


Instructions
------------

### Step 1: Environment

You will need access to a Kubernetes cluster. For testing you can use
[Minikube](https://minikube.sigs.k8s.io/). You can start it like so:

    minikube start \
        --cpus=6 \
        --memory=8g \
        --disk-size=20g \
        --addons=registry \
        --feature-gates=SCTPSupport=true

We will be using [Reposure](https://github.com/tliron/reposure) to run a container image registry in the
cluster. To install it and set it up for Minikube's registry add-on:

    reposure operator install --role=view --wait -v
    reposure registry create default --provider=minikube --wait -v

### Step 2: Build

The build scripts assume you are running on Fedora. If you don't have access to a baremetal Fedora
machine you can use our [Vagrant](https://www.vagrantup.com/) configuration that will set up a virtual
machine for you. To use it, change into this repository's directory and run:

    vagrant up
    vagrant ssh
    cd /vagrant

1. install-build-dependencies
2. build-distribution
3. build-container-image
4. publish-container-image

### Step 3: Deploy

1. deploy-mongodb (uses the [MongoDB community operator](https://github.com/mongodb/mongodb-kubernetes-operator))
2. generate-configs
3. deploy-configs
4. deploy-certificates (uses [cert-manager](https://github.com/jetstack/cert-manager))
5. deploy-open5gs

### Utilities

To get the webui URL:

    ./webui-url

The default user is "admin" and the default password is "1423".

You can see the logs of any component:

    ./log mme

And also get a shell to a container for debugging:

    ./shell mme


TODO
----

* Restart components when configmaps are updated
* Make the [Reposure](https://reposure.puccini.cloud/) requirement optional
