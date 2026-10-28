---
title: "Ethical Hacking Club"
---

# Ethical Hacking Topic

## About Us

Ethical Hacking Club is all about red teaming! We have a primary focus of preparing for the annual Collegiate Penetration Testing Competition, but anyone can come and learn even if you have no intention of joining the DSU CPTC Team. We will be putting our knowledge to the test by using platforms such as TryHackMe, HackTheBox, etc. to practice ethical pen-testing. Get ready to dive into the exciting world of ethical hacking. See you there!

## Our Leader

Rayn Light

## Meeting Information

### Meeting Times

***Regular meetings:*** Normal Computer Club meeting times, Tuesday and Wednesday from 6-7 pm CST

### Getting Started

***Accounts:*** If this is your first time attending and you want to jump right in, please consider making an account with both [HackTheBox](https://www.hackthebox.com/) and [TryHackMe](https://tryhackme.com/) ahead of time. These platforms also allow you to utilize VPN access rather than a cloud-based VM for each lab.

***Tools:*** I highly recommend you consider running your own hacking system in a virtual machine. If you want a good baseline, I recommend running a hypervisor such as [VirtualBox](https://www.virtualbox.org/) picking up a [Kali Linux](https://www.kali.org/get-kali/#kali-virtual-machines) image such as the VM link provided.

***OpenVPN:***

*Quick Note about VPNs:* If you are using a local virtual machine, you can run your VPN on your host machine and change your VM interface to run through a NAT configuration instead. This allows both your VM and your Host machine to reach out to the lab.

***VPN Access:*** Both HackTheBox and TryHackMe utilize OpenVPN in order to connect externally to their network. On TryHackMe, you can click on your profile picture and go to the access menu. Go ahead and download a Machines VPN configuration. For HackTheBox, when you sign in you should see a "Connect to HTB" button in the upper right side of your dashboard. Once again, go ahead and download a machines VPN configuration.

- For **Windows**, please install the [OpenVPN Connect Client](https://openvpn.net/client-connect-vpn-for-windows/). This is a graphical application that can help you manage your active VPN configurations. Open up the OpenVPN Connect app and press the plus in the lower right. Browse to your downloaded configuration file to import it. Once you have added your config file, you should be able to switch it on and connect to the VPN network

- For **Linux** (version specific), open your terminal. For those of you on Debian based systems, you can use a command such as `sudo apt install openvpn`. Once that is complete, you can use a command structured like `sudo openvpn --config <PATH TO CONFIG>` in order to start your connection. This command will pause when complete and not drop you back to a command line.
