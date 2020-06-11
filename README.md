# ansible_docker_repo
Ansible Repository for testing ansible using test kitchen with Docker.
The tests are stored in the in /test/integration (as in the chef format)

This demonstrates using test-kitchen, ansible and kitchen-verifier-serverspec to build and verify a server.

## Workstation Software Installation

The first thing you need to do is install the test-kitchen environment on your workstation.
A useful link is: http://misheska.com/blog/2013/12/26/set-up-a-sane-ruby-cookbook-authoring-environment-for-chef/

The follow instructions are for Windows PC (it will be similar for Mac):

1. Download and install virtualbox from https://www.virtualbox.org/wiki/Downloads.
2. Download and install Docker
3. Download and install the Windows RubyInstaller for 64 bit Ruby 2.x from http://rubyinstaller.org/downloads.
   * Check the option to add ruby to your path.
   * Install the devkit
4. Then install the following gems
  * gem install test-kitchen
  * gem install kitchen-ansible
  * gem install kitchen-docker
  * gem install kitchen-verifier-serverspec
7. git clone the repository https://github.com/neillturner/ansible_docker_repo

## Check everything installed

In a Docker CLI window in the puppet_docker_repo directory run command
```
kitchen list
```
NOTE: I used Windows Kitematic and select Docker CLI from the bottom of the screen to get a Docker CLI Powershell Window
This will return a list if everyting is correctly installed.


## Create Servers in Docker on your Workstation.
```
kitchen create ansible-centos-8 -l debug
```

## Build the server.
```
kitchen converge ansible-centos-8 -l debug
```

## Verify the server.
```
kitchen verify ansible-centos-8 -l debug
```

## Destroy the server.
```
kitchen destroy ansible-centos-8 -l debug

```
## References

https://michaelheap.com/test-kitchen-docker-and-centos-7/
