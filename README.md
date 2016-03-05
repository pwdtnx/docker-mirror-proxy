# docker-mirror Vagrantfile

A Vagrantfile to construct a simple docker resistry proxy cache.

## Requirement
- VirtualBox
- Vagrant
- vagrant-vbguest plugin (or mount will fail)
- vagrant-docker-compose plugin
- Ansible

## Usage
- `vagrant up`
- add `--insecure-registry <Vagrant Host>:5000 --registry-proxy http://<Vagrant Host>:5000` to `docker daemon` startup options (see <https://docs.docker.com/engine/admin/configuring/>)
- `docker pull` to get images you like
- access http://\<Vagrant Host\>:8080/ to see the images you pulled are in your registry
