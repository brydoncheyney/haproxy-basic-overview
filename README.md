# HAProxy Overview

> The Reliable, High Performance TCP/HTTP Load Balancer

## Demo

Demo to show HAProxy environment and configuration.

## Requirements

- [vagrant](https://www.vagrantup.com/)
- [lxc](https://linuxcontainers.org/)

### lxc-net

To enable lxc-net DNS name resolution of lxc subdomains add the following entry
to `/etc/default/lxc-net`

    LXC_DHCP_CONFILE=/etc/dnsmasq.conf

## Usage

To provision the haproxy load balancer and backend servers:

    vagrant up

This creates the following containers:

    vagrant status
    Current machine states:

    haproxy                   running (lxc)
    a                         running (lxc)
    b                         running (lxc)

To setup dns resolution for wildcard \*.haproxy.lxc hosts:

    sudo ./haproxy-dns

To see requests directed to backend servers using ACL rules based on host
subdomain:

    curl http://a.haproxy.lxc
    curl http://b.haproxy.lxc

To see requests load balanced across all backend servers:

    curl http://haproxy.lxc

To simulate load across all backend servers:

    ./simulate-load [SECONDS]

stop the simulation with  &lt;Ctrl>-C!

## Slides

[HAProxy presentation slides](https://slides.com/brydon/haproxy)

Copyright (c) Brydon Cheyney
