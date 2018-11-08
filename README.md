# packer_nginx64
Packer template for creating Vagrant VirtualBox Box

# Prerequisites: 

* **Packer** - you could obtain it from [here](https://www.packer.io/downloads.html)
* **Oracle VirtualBox** - you could obrain it from [here](https://www.virtualbox.org/wiki/Downloads)
* **Vagrant** - you could obtain it from [here](https://www.vagrantup.com/downloads.html)

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
- After all processes are finished, you will have the following artifact: ```nginx64```. 

## Testing the box that is backed by packer with Kitchen

**NOTE** The following instructions are intended for MacOS users!

# Prerequisites: 

 * Install and fine tune rbenv by running the following commands
   
```
which rbenv || brew install rbenv

grep ".rbenv" ~/.bash_profile || {
  echo 'export PATH="$HOME/.rbenv/bin:$PATH"' | tee -a ~/.bash_profile
}

source ~/.bash_profile

rbenv init
```
 * Install ruby version 2.3.1 with rbenv by running the following commands

```
rbenv versions | grep 2.3.1 || rbenv install 2.3.1

rbenv local 2.3.1

```

 * Install bundler
 
 ```
 gem install bundler
 ```
 * Run the following command: 
 
 ```
 # This will install all gems described in the Gemfile
 
 bundle install
 ```

# Testing phase: 

- First, make the box that we built available to Vagrant by adding it: 

```
vagrant box add --name nginx64 nginx64.box
```

- To perform the testing, run the following command: 

``` 
bundle exec kitchen test
```

- If the test is scuccessful, you shoud see an output similar to the on the picture below: 
![Alt text](pics/Success.png?raw=true "Successful test")
