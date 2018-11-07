# packer_nginx64
Packer template for creating Vagrant VirtualBox Box

# Prerequisites: 

* **Packer** - you could obtain it from [here](https://www.packer.io/downloads.html)
* **Oracle VirtualBox** - you could obrain it from [here](https://www.virtualbox.org/wiki/Downloads)

# What is this Repository about

This repo contains a Packer template which will create a Vagrant box for use with Oracle's VirtualBox. 
The template uses provisioning script which will install nginx server, making it available immediately afte the machine is powered-on. 

Additionally, the repository contains configuration for kitchen-test as well as a test, which will check if nginx is installed in the final artifact. 

## How to use this repository

- Clone this repository

```
git clone https://github.com/firedot/packer_nginx64.git
```

- Go in the repository directory

```
cd packer_nginx64
```

- Run the following command

```
packer build template.json
```

