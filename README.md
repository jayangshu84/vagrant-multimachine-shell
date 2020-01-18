# Vagrant multi-machine setup with Nginx as load balancer using shell as provisioner

## Usage

To create the entire environment:
- Unzip the zip file in your local directory and run the commands below
- `$ cd vagrantTest`
- `$ vagrant up`

To view the app:
- The app can be accessed via any web browser at [http://10.0.0.10/](http://10.0.0.10/) after completeing above three steps

This will create 3 virtual machines -- 1) Load balancer: lb1; 2) Two web servers: web1 & web2. All three machines are running Nginx.

## Prerequisites / Requirements

- [Virtualbox platform](https://www.virtualbox.org/wiki/Downloads) (Tested with version 6.0.14)
- [Vagrant](https://docs.vagrantup.com/v2/installation/) (Tested with version 2.2.6)

## OS for the VMs

- Ubuntu x64 Bionic image from [Hashicorp](https://app.vagrantup.com/ubuntu/boxes/bionic64)

## Solution

In this solution, I am using Vagrant "shell" provisioner to configure the entire environment.
- Two shell script: 1) provision-lb.sh and 2) provision-web.sh for load balancer & web respectively
- provision-lb.sh is being used in line 20 `lb1.vm.provision "shell", path: "./provision-lb.sh"` for configuration of load balancer
- provision-web.sh is being used in line 28 & 38 `shell.path = "./provision-web.sh"` for configuration of web servers
- In line 27 & 37, I am passing shell arguments to automatically create the html file.


## Compromises

Due to time constrains, my solution is very simple that demostrates a simple load balanced environment:
- No configuration management using ansible, puppet, chef, etc.
- A simple webapp showing a html file
- No databased behind the app tier

## Improvements

Happy to make following improvements if the attached solution doesn't work:

- A complex webapp that queries data from a database
- A database with some initial data created using a configuration management tool such as ansible
- Use of actual configuration management tool as provisioner
