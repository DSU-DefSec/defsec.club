---
title: "CyberConquest"
---

# CyberConquest

Cyber Conquest is a purple-team cybersecurity competition (that is, it combines both offensive and defensive skillsets) into one king-of-the-hill contest. Teams are tasked with defending their own infrastructure while attacking other team’s infrastructure to gain points. Defensive points are gained by keeping your services up and keeping other teams off your systems, and offensive points are gained by planting your flag on opponent’s systems.

Successful teams will consist of both attackers and defenders. Teams must communicate and work together to as effective as possible. While good offense informs defense, good defense also informs offense.

## Defense (Blue)

Each team will be given console access to systems that they are responsible for. Similar to defensive competitions like CCDC, each of these systems will be running a set of services that must be maintained in order to gain defender points. Defenders are tasked with securing these systems while maintaining service uptime. A large part of securing these systems will consist of seeking out and destroying enemy persistence. All teams will start with nearly identical systems, so as a secondary objective, defenders should look for vulnerabilities in their systems which their attacker teammates can exploit on other teams.

## Attack (Red)

Each team will be given a token. To earn attacker points, the team must hit the scoring engine with that token (via curl, wget, etc). The goal is not to destroy systems but rather to stealthily gain access and plant persistence. Therefore, offensive and defensive points are only awarded if a system’s services are online and functioning.

### Persistence Points

Hit the scoring engine with an HTTP GET request at where here TOKEN is your team token that we've given to you, and that IP is the scoring engine. `http://10.30.0.100/persist/TOKEN` You must request that URL from the machine that you've hacked. The engine determines what machine you're on based on its IP address. For example, if your token was soup, you'd prove persistence like this:

```bash
curl http://10.30.0.100/persist/soup
```

Or on Windows (powershell):

```powershell
Invoke-WebRequest -Uri http://10.30.0.100/persist/soup
```

See the [scoring engine](https://scoring.defsec.club) for more competition-specific information.

More information can also be found on <https://cyberconquest.org>.

## DakotaCon 10.1 Cyber Conquest

- [Infrastructure write up by Gaelin](https://blog.gael.in/cyberconquest)
