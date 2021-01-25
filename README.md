# Docker Swarm Bootstrap with Vagrant

This repo gives a simple example on how to set up a 3 nodes Docker Swarm cluster using Vagrant and Ansible.
The configuration is customisable to suit different needs.

This cluster is intended for development purpose only and should not be used as a production environment.

## Prerequisites

- [vagrant](https://www.vagrantup.com/docs/installation)
- [ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html)
- [docker](https://docs.docker.com/engine/install/) (The `docker-cli` is required)

## Installation

```sh
vagrant up

cd playbooks
ansible-playbook swarm.yml
```

## Usage

The cluster will expose the unencrypted docker socket and port forward it to the port 2378 on your host.
Updating the `DOCKER_HOST` environment variable in the host's shell will allows execution of `docker` commands without the need to connect to the cluster nodes via ssh.

This repo includes two examples of docker compose file for [Traefik](https://github.com/traefik/traefik) and [portainer](https://github.com/portainer/portainer).

```sh
export DOCKER_HOST=tcp://127.0.0.1:2378

cd stacks
docker stack deploy -c traefik.yml traefik
docker stack deploy -c portainer.yml portainer
```
