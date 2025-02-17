# LinuxCNC EtherCAT Introduction

_This repo and its author(s?) aren't affiliated with LinuxCNC._

## Why am I qualified to make this document?

I'm not. I started this document one week after I spun up my first LinuxCNC computer and started learning it. But I struggled a lot and I'm hoping I can consolidate a handful of resources to make it easier for others to learn.

## Overview

This guide will focus on using Beckhoff hardware as that is what I have collected. However, I'll aim to make this generic where possible. 

This guide also assumes you're familiar with linux both from a desktop environment and the command line. 

I would also like to encourage you, yes _you_ to contribute to this repo! Please point out mistakes, make suggestions, or even open pull requests!

## Outline
* [Resources](#resources)
* [Examples](#examples)

### Resources

Here are some great resources you should keep in mind when trying to learn or when you need to look something up

#### [LinuxCNC Docs](https://linuxcnc.org/docs/stable/html/)
I _must_ say that the LinuxCNC docs page is glorious. As a beginner to LinuxCNC I found it nearly overwhelming, but as I've been learning it has become instrumental in my understanding of LinuxCNC.

#### [LinuxCNC Ethercat Forum](https://forum.linuxcnc.org/ethercat)
This community has a ton of great people that go out of their way to help. I've found a ton of great information in the various posts and converasations.

#### [LinuxCNC Ethercat Docs](https://linuxcnc-ethercat.github.io/linuxcnc-ethercat/)
While a little sparse, once you get off the ground you'll likely find these docs very helpful.

#### [LinuxCNC Ethercat Repo](https://github.com/linuxcnc-ethercat/linuxcnc-ethercat/tree/master)
This repository also contains a ton of excellent documentation.

## Examples

* [Basic Digital Outputs](basic_digital_outputs/readme.md)
  * A demonstration of how to use a HAL config to control a digital output
* [EL7041 Stepper Motor Example](el7041_stepper_motor_example.md)
  * A demonstration of how to configure the titular software `linuxcnc` to control a stepper motor


# Credits / Thanks
* Rodw
* Hakan
* `linuxcnc-ethercat` devs
* [exgif.com](https://ezgif.com/) for making converting `.mp4`s into gifs easy