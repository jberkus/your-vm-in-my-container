background-image: url(choc1.jpg)

#### You Got Your VM<br />In My Container

.sigblock[
Josh Berkus<br />
Jason Brooks<br />
Red Hat OSAS<br />
SCALE 16x
]

.leftlogo[![redhat logo](red_hat_dingbat.png)]

---

# VMs-in-containers

---

Why would we want this?

---

VMs are awesome, but...

They require infra like shared storage, and HA management services

---

My Lab: 

Hyper-Converged oVirt + Gluster

---

Enter Kubernetes

I get to thinking about *more* convergence...

---

background-image: url(kube-wheel.png)

---

A lot of it worked: 

Storage, Management, Authentication

---

Virtualization? 

Way too janky, so I punted...

---

Container-native storage has continued to progress

* Gluster CNS
* Ceph (Rook)

---

# KubeVirt

*an add-on that extends kubernetes to support scheduling of VM workloads alongside container workloads*

![kubevirt](kubevirt-pre.svg)

---

# KubeVirt Anatomy

---

Custom Resource Definitions

* New virt-specific object types added to the kube apiserver
* Manage like other kube objects, using kubectl

---

virt-controller

* A kubernetes operator
* Watches the apiserver for VM objects
* Creates pods for new VMs to like in

---

virt-handler

* One of these runs on every node
* Takes over the VM pod once the virt-controller creates it
* Starts up libvirt inside the pod

---

virt-launcher

* Each VM gets a virt-launcher pod
* This is the pod that the virt-controller creates initially, and the virt-handler takes over

---

storage

* pv volumes
* ephemeral volumes
* registry disk volumes
* cloud-init nocloud volumes

---

networking

* Regular pod networking
* Every kubernetes pod gets its own IP
* Expose ports with kube services

---

# Demo

---

# ¿questions?

.left-column-narrow[
more<br />jberkus:

jbrooks:

Red Hat:

&nbsp;
]

.right-column-wide[
@fuzzychef<br />
www.databasesoup.com<br />
jberkus.github.io

@jasonbrooks

community.redhat.com

&nbsp;
]

.leftlogo[![rh logo](red_hat_dingbat.png)]

.rightlogo[![cc by sa](by-sa.png)]
