# Au70's LinuxCNC EtherCAT Introduction

## Why am I qualified to make this document?

I'm not. I started this document one week after I spun up my first LinuxCNC computer and started learning it. But I struggled a lot and I'm hoping I can consolidate a handful of resources to make it easier for others to learn. 

## Overview

This guide will focus on using Beckhoff hardware as that is what I have collected. However, I'll aim to make this generic where possible. 

This guide also assumes you're familiar with linux both from a desktop environment and the command line. 

I would also like to encourage you, yes _you_ to contribute to this repo! Please point out mistakes, make suggestions, or even open pull requests!

## Outline
* [Resources](#resources)
* [Required Reading Part 1](#required-reading-part-1)
* [Linuxcnc Ethercat setup](#linuxcnc-ethercat-setup)
* [Basic Digital Outputs](#basic-digital-outputs)
* [Required Reading Part 2](#required-reading-part-2)
* [Stepper Motor Control](#stepper-motor-control)

## Resources

Here are some great resources you should keep in mind when trying to learn or when you need to look somethin gup

### [LinuxCNC Docs](https://linuxcnc.org/docs/stable/html/)
I _must_ say that the LinuxCNC docs page is glorious. As a beginner to LinuxCNC I found it nearly overwhelming, but as I've been learning it has become instrumental in my understanding of LinuxCNC.

### [LinuxCNC Ethercat Forum](https://forum.linuxcnc.org/ethercat)
This community has a ton of great people that go out of their way to help. I've found a ton of great information in the various posts and converasations.

### [LinuxCNC Ethercat Docs](https://linuxcnc-ethercat.github.io/linuxcnc-ethercat/)
While a little sparse, once you get off the ground you'll likely find these docs very helpful.

### [LinuxCNC Ethercat Repo](https://github.com/linuxcnc-ethercat/linuxcnc-ethercat/tree/master)
This repository also contains a ton of excellent information.

## Required Reading Part 1

I'm not your real dad, I have no authority over you. But if you're starting out your journey into LinuxCNC it would do you well to grok the resources I've linked above and especially below. Some of these felt buried and hard to discover, so I'm doing my best to bring them to light.

### [Ethercat installation from repositories - how to step by step](https://forum.linuxcnc.org/ethercat/45336-ethercat-installation-from-repositories-how-to-step-by-step)

Rodw has an excellent post that details how to configure `linuxcnc-ethercat` for use with LinuxCNC. His post covers the basic installation required to get going. Read it and follow it step-by-step.

###  [HAL Tutorial](https://linuxcnc.org/docs/stable/html/hal/tutorial.html)
This tutorial does a great job of introducing HAL, and HAL tools including `halshow` and `halscope`.

## LinuxCNC Ethercat Setup
Hopefully this is pretty boring and straightforward. 
1. Follow the [post by Rodw](https://forum.linuxcnc.org/ethercat/45336-ethercat-installation-from-repositories-how-to-step-by-step) and make sure you can run the command `ethercat slaves` successfully

```bash
paul@Precix:~$ ethercat slaves
0  0:0  PREOP  +  EK1101 EtherCAT-Koppler (2A E-Bus, ID-Switch)
1  0:1  PREOP  +  EL2024 4K. Dig. Ausgang 24V, 2A
2  0:2  PREOP  +  EL1018 8Ch. Dig. Input 24V, 10�s
3  0:3  PREOP  +  EL7041 1K. Schrittmotor-Endstufe (50V, 5A)
```
_note: your output will almost certainly be different from mine_


## Required Reading Part 2

### [Ethercat 64 bit stepper drive basic example EL7041](https://forum.linuxcnc.org/27-driver-boards/35717-ethercat-64-bit-stepper-drive-basic-example-el7041#319333)

This one can wait for later as it's more advanced, but I was able to take the example provided by Grotius and finally get an EL7041 to work for me. 


### [LinuxCNC Ethercat Docs - EL7041](https://linuxcnc-ethercat.github.io/linuxcnc-ethercat/el7041.html)
This page demonstrates ways to configure the EL7041 modules directly from the XML.

