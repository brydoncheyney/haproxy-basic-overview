# HAProxy Overview

> The Reliable, High Performance TCP/HTTP Load Balancer

## Demo

Demo to show HAProxy environment and configuration.

## Requirements

- [vagrant](https://www.vagrantup.com/)
- [https://linuxcontainers.org/](lxc)
- DNS configuration to resolve lxc subdomains (`dnsmasq`, `/etc/hosts`, etc)

## Usage

To bring up and configure the haproxy load balancer and backend servers:

    vagrant up

To see requests directed to backend servers using ACL rules based on host subdomain:

    curl http://a.haproxy.lxc
    curl http://b.haproxy.lxc

To see requests load balanced across all backend servers:

    curl http://haproxy.lxc

## Slides

[HAProxy presentation slides](https://slides.com/brydon/haproxy/edit)

Copyright (c) Brydon Cheyney
