name: inverse
layout: true
class: center, middle, inverse-red

---
## Multi-Cluster Management with Rancher

---
exclude: true
layout: false
### whoami

.left-small[
    ![image](https://pbs.twimg.com/profile_images/994762110792953856/EheEvqBY_400x400.jpg)
]

.right-large[
- Kyohei Mizumoto(@kyohmizu)

- C# Software Engineer

- Interests
    - Docker/Kubernetes
    - Go
    - Security
]

---
layout: false
### Target

- People who:

    - haven't used Rancher

    - are interested in multi-cluster management

---
### Preferred

- The basic knowledge of:

    - Docker

    - Kubernetes

    - Cloud platform(e.g. AKS, GKE)

---
### Agenda

- What is Rancher?

- Get Started on Azure

- Create Clusters

- Demo

---
class: center, middle, inverse-red
## What is Rancher?

---
### Docker

- Container packaging and runtime standard

- Build container images from Dockerfiles

- Distribute container images from Docker registries

<center><img src="https://www.docker.com/sites/default/files/social/docker_facebook_share.png" width=35%></center>

---
### Kubernetes

- Container cluster management standard

- Open source software

- Cloud Native Computing Foundation(CNCF) hosts

<center><img src="https://upload.wikimedia.org/wikipedia/en/0/00/Kubernetes_%28container_engine%29.png" width=27%></center>

---
### Rancher

- Container(Kubernetes) management platform

- Open source software

- Deliver Kubernetes as a Service(KaaS)

<center><img src="https://rancher.com/img/brand-guidelines/assets/logos/png/color/rancher-logo-stacked-color.png" width=45%></center>

---
### Run Kubernetes Everywhere

- Create Kubernetes clusters with:

    - Rancher Kubernetes Engine (RKE)

    - Cloud Kubernetes services(e.g. GKE, AKS, EKS)

-  Import & manage existing Kubernetes clusters

---
### Empower DevOps Teams

- Each team deploys their applications on the public/ private clouds they choose

<center><img src="https://rancher.com/docs/img/rancher/platform.png" width=100%></center>

---
### Architecture

<center><img src="https://rancher.com/docs/img/rancher/rancher-architecture.png" width=90%></center>

---
### Architecture

- Rancher API Server

- Cluster Controller and Agents

- Authentication Proxy

---
class: center, middle, inverse-red
## Get Started on Azure

---
### Installation

- Single Node Install

    - Install by running a single Docker container

    - For development and testing environments

- High Availability (HA) Install

    - Install in a Kubernetes cluster

    - For production environments

---
### Installation

- Single Node Install

    - Install by running a single Docker container

    - For development and testing environments

.color-gray[
- High Availability (HA) Install

    - Install in a Kubernetes cluster

    - For production environments
]

---
class: header-margin
### Create VM on Azure

<center><img src="vm.png" width=100%></center>

---
### Install

- ssh to the VM

- Install Docker with the following command:

.zoom1[
```bash
$ curl https://releases.rancher.com/install-docker/18.09.sh | sh
```
]

- Install Rancher with the following command:

.zoom1[
```bash
$ sudo docker run -d --restart=unless-stopped -p 80:80 \
  -p 443:443 rancher/rancher:v2.2.2
```
]

---
### Access to VM

```yaml
https://[IP address of VM]
```

<center><img src="welcome-rancher.png" width=100%></center>

---
### Settings

- Set a password

- Save the URL(default)

---
class: header-margin
### Done :)

<center><img src="portal.png" width=100%></center>

---
class: center, middle, inverse-red
## Create Clusters

---
## Create Clusters

- Custom

- GKE

- Azure

---
class: center, middle, red
## Custom

---
### Advance Preparation

- Create an another VM for node on Azure

```yaml
name: rancher-node
image: Ubuntu Server 18.04 LTS
OS-disk-type: Standard SSD
auto-shutdown: off

```

- Add inbound port rules

    - 22, 443

---
class: header-margin
### Choose Custom

<center><img src="custom.png" width=100%></center>

---
### Set IPs of VM

<center><img src="custom2.png" width=90%></center>

---
### Create a Cluster

- Run the copied command on VM

.zoom0[
```bash
$ sudo docker run -d --privileged --restart=unless-stopped --net=host \
  -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run rancher/rancher-agent:v2.2.2 \
  --server https://xx.xx.xxx.xx --token 666ltr6qntjz2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx \
  --ca-checksum f707d53266d14e03ff3452896dxxxxxxxxxxxxxxxxxxxxxxxxxxx --address xx.xx.xxx.xx \
  --internal-address 10.x.x.x --etcd --controlplane --worker
```
]

---
class: header-margin
### Provisioning...

<center><img src="custom3.png" width=100%></center>

---
class: center, middle, inverse-red
## Demo

---
### Links

.zoom1[
マルチクラウド時代の最強コンビ　RancherによるKubernetes活用ガイド  
<u><https://thinkit.co.jp/series/8740></u>

Official - Rancher 2.x  
<u><https://rancher.com/docs/rancher/v2.x/en/></u>

]