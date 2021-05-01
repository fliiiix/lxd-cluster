LXD Cluster
===========

LXD supports clustering (see https://lxd.readthedocs.io/en/latest/clustering/). 

> LXD can be run in clustering mode, where any number of LXD servers share the same distributed database and can be managed uniformly using the lxc client or the REST API.

This project provides a lxd cluster with three nodes (`server1`, `server2` and `server3`). Where `server1` is our bootstrap node and 
the other two are member nodes.

## Pre requisites 

```
ansible-galaxy collection install community.general
```

If you know how to automatically install that with vagrant,
please let me know!

## Run

Run with:

```
vagrant up
```

## Cleanup

Stop and remove all VMs.

```
vagrant destroy -f
```

## Use in the real world

To use this ansible role in a real world setup,
I would recommended to use at least a different certificate.
Just generate a new `lxd.crt` and `lxd.key` in `ansible/roles/lxd/files`.

For example with this openssl command:

```
openssl req -x509 -newkey rsa:4096 -sha256 -days 3650 -nodes \
  -keyout lxd.key -out lxd.crt -subj "/CN=192.168.10.10" \
  -addext "subjectAltName=DNS:server1,IP:192.168.10.10"
```

