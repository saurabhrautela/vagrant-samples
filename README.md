# Sample Vagrant files
Quickly setup single or multiple virtual machines with the desired configuration.

## What is [Vagrant](https://www.vagrantup.com/)?
>Vagrant is a tool for building and managing virtual machine environments in a single workflow. With an easy-to-use workflow and focus on automation, Vagrant lowers development environment setup time, increases production parity, and makes the "works on my machine" excuse a relic of the past.

## Why?
* Configurable
* Reproducible
* Portable
* Easy to use

## Get Started
### Quick Start
1. Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. Clone this repository
4. Make the desired changes to the Vagrant files
5. Run command: `vagrant up`
6. Run command: `vagrant ssh <instance_name>`

### Some common Commands
1. __vagrant init__:  Initialize the current directory to be a Vagrant environment by creating an initial Vagrantfile.
2. __vagrant status__: Check the state of machines managed by Vagrant.
3. __vagrant up__: Create and configure virtual machines according to Vagrantfile.
4. __vagrant halt__: Shutdown running virtual machines that managed by Vagrant.
5. __vagrant reload__: Restart virtual machines that are managed by Vagrant.
6. __vagrant ssh <instance>__: SSH into a running virtual machine.
7. __vagrant ssh-config__: Output valid configuration for a SSH config.
8. __vagrant destroy__: Stop the virtual machines and destroy all resources related to the machine.  
_Refer [Vagrant CLI documentation](https://www.vagrantup.com/docs/cli/) for more commands._

### Samples
1. __single_vm__: start a single virtual machine
2. __multi_vm__: start multiple virtual machines (in this case 3)
3. __input_data_in_provision__: input data such as credentials during the creation of virtual machine
