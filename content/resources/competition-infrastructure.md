# Competition Infrastructure

Refer to the [Networks](/resources/ialab/networks/) diagram and information.

## Overview

Each team is given a set of systems behind a pfSense or Palo router/fw. The router does NAT from an internal network (192.168.0.0/24) to an external network (10.20.X.0/24).

## Competition Networks

- Internal team network (LAN) 192.168.0.0/24
- Competition Teams (External) 10.20.X.0/24 (where X is team number)
- Red team 10.30.0.0/16
- VPN 10.31.0.0/16
- Red IP randomizer 10.32.0.0/16

## Important IPS

- Scoring engine: 10.30.0.100
- Upstream DNS: 10.[20/30].0.1
