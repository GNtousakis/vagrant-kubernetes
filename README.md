# Kubernetes Cluster automation

The purpose of this repo is to automate the deployment of an ubuntu VM.

Currently, the base system is:

- ubuntu 20.04
- 8GB ram
- 8 cores
- user = vagrant
- user has passwordless sudo

Provisioning adds the following:

- git
- tig
- vim
- htop
- jq

Bring VM up:

```
vagrant up
```

Halt VMs:

```
vagrant halt
```

Connect to a VM:

```
vagrant ssh ubuntuWorker
```

Full documentation can be found [here](https://www.vagrantup.com/docs/index)

Please check the provided Vagrantfile for further technical details/choices.

