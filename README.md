# Quickstart

## Introduction

In this section, you'll learn how to get up and running with a stand-alone Anchore Enterprise installation for trial, demonstration, and review with [kind](https://kind.sigs.k8s.io/) and [Helm](https://helm.sh/). 

## Prerequisites

- [Docker](https://docs.docker.com/engine/install/)
- [Go (1.11+)](https://golang.org/doc/install)
- [kind](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)
- [Helm](https://helm.sh/docs/intro/install/)

### Step 1: Create required secrets for Anchore Enterprise installation

**Note:** In this example, a dedicated `anchore` namespace is used for the deployment. This is not a requirement for installation.

##### License secret

`kubectl create secret generic anchore-enterprise-license --from-file=license.yaml=<PATH/TO/LICENSE.YAML> -n anchore`

##### Pullcreds secret

`kubectl create secret docker-registry anchore-enterprise-pullcreds --docker-server=docker.io --docker-username=<DOCKERHUB_USER> --docker-password=<DOCKERHUB_PASSWORD> --docker-email=<EMAIL_ADDRESS>`

### Step 2: Install Anchore Enterprise with Helm

```
helm repo add anchore https://charts.anchore.io
helm install anchore anchore/anchore-engine -f values.yaml -n anchore
```

**Note:** The following commands add the Anchore Helm repository and install the Anchore Engine Helm chart in the `anchore` namespace

### Step 3: Verify the install

`helm ls -n anchore`

`kubectl get pods -n anchore`

`kubectl describe ingress -n anchore`


