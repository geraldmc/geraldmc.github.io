---
layout: post
title: Using Docker
#published: false
#tags: ['docker', 'data engineering']

---

### What Is Docker?

Docker is an open platform that both operations and developers use to build, test and ship applications. The platform facilitates agility by providing an easy way for team members to package applications into standard containers. A `container` provides everything an app needs to run *and nothing more*. 

---

### How is a Docker container different from a VM?

The Docker engine is a software component that is installed on any physical, virtual, or cloud host with [a compatible OS](http://linuxbsdos.com/2015/04/04/6-operating-systems-designed-just-for-docker-and-other-container-runtimes/). This component leverages the host kernel such that it runs multiple root file systems (containers) each sharing the host kernel. Docker containers do not replicate the full OS (unlike VMs). Instead they share the underlying kernel, running isolated and unaware of one another. Docker Networking can be used to create a multi-host network that enables containers to talk to one another but this is not a requirement.

Docker containers do not package up the OS. Instead they package the application with all the OS-level services required for that application to run. Docker containers do not replace traditional VMs, they compliment them. 

---

### What are the benefits?

Developers love Docker because it lets them quickly build and ship new applications. Since containers are portable and can run in most any environment (with a Docker Engine installed) developers go from dev, to test, to staging and production without a blip, without recoding. Docker containers makes it easier for developers to debug, update images and ship them.

Ops teams love Docker because it lets them more easily manage and secure their environments (while allowing developers to adopt a more self-service style). The [Docker CaaS platform](https://blog.docker.com/2016/02/containers-as-a-service-caas/) deploys on-site and features security hooks such as role-based access control, LDAP integration, image signing, and more.

---

### What is the infrastructure cost?

The Docker engine itself is lightweight (around 80 MB total) and is the only required component (installed on a bare metal server, a VM, or in the cloud). Install the engine and you're done.

---

### Can Docker help manage my infrastructure?

Docker isn’t designed to manage infrastructure (the platform itself is infrastructure agnostic). Instead, it *manages applications* and helps ensure that they'll run smoothly, regardless of infrastructure. This provides the agility, portability and control necessary to forget about infrastructure. What you can't forget about your team is still responsible for.

---

### How many containers may be run per host?

The answer depends on your environment, the size of your application and the amount of available resources (i.e. CPU). Containers don't magically create new CPUs though they do provide a more efficient way of utilizing them. Containers are lightweight and often last only as long as the process they run.

---

### Getting started

An easy way to get started with Docker is with [Docker for Mac](https://www.docker.com/products/docker#/mac) (or [Docker Windows](https://www.docker.com/products/docker#/windows)). Each provides a native installation and from here you'll start by creating a `Dockerfile`. This is the blueprint of a Docker Image, where all application configurations are specified.

One misconception about Docker is a by-product of its current focus on microservices. Docker is great for microservice-based apps, but it works just as well to containerize large applications. Docker containers package any application (monolithic or distributed) and can migrate workloads to any infrastructure.


---
