---
layout: post
title: Docker 4 Mac
#published: false
#tags: ['docker', 'data engineering']

---

### What is Docker?

Docker is an open platform that both operations and developers can use to build, run and ship  applications. Docker encourages agility by offering portability and control. Teams can create a standard Docker container to package up an application, provide everything that that application needs to run efficiently *and nothing more*. This allows teams to `containerize` their applications and run them in any environment or infrastructure.

---

### How is a Docker container different from a VM?

The Docker engine is a software component that is installed on a physical, virtual or cloud host with [a compatible OS](http://linuxbsdos.com/2015/04/04/6-operating-systems-designed-just-for-docker-and-other-container-runtimes/). This component leverages the host kernel such that it runs multiple root file systems - called `containers` - each sharing the host kernel. Docker containers do not replicate the full OS (unlike VMs). Instead they share the underlying kernel, running completely isolated and unaware of one another. Docker Networking can be used to create a multi-host network that enables containers to talk to one another but this is not a requirement.

Docker containers do not package up the OS. Instead they package the application with all the OS-level services required for that application to run. Docker containers do not replace traditional VMs, they compliment them. 

---

### What are the benefits?

Developers love Docker because it lets them quickly build and ship new applications. Since containers are portable and can run in most any environment (with a Docker Engine installed) developers go from dev, to test, to staging and production without a blip, without recoding. Docker containers makes it easier for developers to debug, update images and ship to clients.

Ops teams love Docker because it lets them more easily manage and secure environments (while allowing developers to adopt a more self-service style). The [Docker CaaS platform](https://blog.docker.com/2016/02/containers-as-a-service-caas/) deploys on-site and features security hooks like role-based access control, integration with LDAP, image signing, and more.

---

### What is the infrastructure cost?

The Docker engine itself is a very lightweight (around 80 MB total) component that is installed on a bare metal server, a VM or in the cloud. This is the only infrastructure needed.

---

### Can Docker help manage my infrastructure?

Docker isn’t designed to manage infrastructure (the platform itself is infrastructure agnostic). Instead, it *manages applications* and helps to ensure that apps run smoothly, regardless of infrastructure. This provides the agility, portability and control necessary to forget about infrastructure. What you can't forget about your team is still responsible for.

---

### How many containers may be run per host?

The answer depends on your environment, the size of your application and the amount of available resources (i.e. CPU). Containers don't magically create new CPUs though they do provide a more efficient way of utilizing them. Containers are lightweight and often last only as long as the process they run.

---

### What is Docker 4 Mac?

An easy was to get started with Docker is to download [Docker for Mac](https://www.docker.com/products/docker#/mac) (or [Docker Windows](https://www.docker.com/products/docker#/mac)). Each is a newly-native installation of Docker. From here you can start by creating a `Dockerfile`. This is where all application configurations are determined and is the blueprint for a Docker Image.

One misconception about Docker is a by-product of its current focus on microservices. Docker is great for microservice-based apps, but it can just as well be used to containerize large monolithic applications. Docker containers package any application (monolithic or distributed) and can migrate workloads to any infrastructure.


---
