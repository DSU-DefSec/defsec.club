---
title: "DefSec VPN"
---

# DefSec VPN

We run a VPN to allow for network level access into the [IALab](/resources/ialab/).

You will be assigned a *10.31.0.1/16* address. This VPN is split tunnel meaning that only select traffic will be forwarded through it. Only the [org networks](/resources/ialab/networks/) as well as DNS are forwarded through the tunnel. DNS is not necessary however it allows for custom records such as *scoring.engine*. Regular internet traffic is not forwarded through the tunnel.

## Connecting

We use OpenVPN which requires a client and a profile to connect.

### Client

The client can be downloaded from [openvpn.net](https://openvpn.net/vpn-client/).

### Profile

A profile file (.ovpn) will be sent in [Discord](https://discord.defsec.club) shortly before any competition beings or upon request.
