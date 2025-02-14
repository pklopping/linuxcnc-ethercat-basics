# Au70's LinuxCNC EtherCAT Introduction

## Why am I qualified to make this document?

I'm not. I started this document one week after I spun up my first LinuxCNC computer and started learning it. But I struggled a lot and I'm hoping I can consolidate a handful of resources to make it easier for others to learn. 

## Overview

This guide will focus on using Beckhoff hardware as that is what I have collected. However, I'll aim to make this generic where possible. 

This guide also assumes you're familiar with linux both from a desktop environment and the command line. 

I would also like to encourage you, yes _you_ to contribute to this repo! Please point out mistakes, make suggestions, or even open pull requests!

## Outline
* [Required Reading Part 1](#required-reading-part-1)
* [linuxcnc-ethercat setup](#linuxcnc-ethercat-setup)
* [Basic Digital Outputs](#basic-digital-outputs)
* [Required Reading Part 2](#required-reading-part-2)
* [Stepper Motor Control](#stepper-motor-control)

## Required Reading Part 1

I'm not your real dad, I have no authority over you. But if you're starting out your journey into LinuxCNC it would do you well to grok the resources I link to below. Some of these felt buried and hard to discover, so I'm doing my best to bring them to light.

### [LinuxCNC Docs](https://linuxcnc.org/docs/stable/html/)
I _must_ say that the LinuxCNC docs page is glorious. As a beginner to LinuxCNC I found it nearly overwhelming, but as I've been learning it has become instrumental in my understanding of LinuxCNC.

In particular the HAL section, especially the [HAL Tutorial](https://linuxcnc.org/docs/stable/html/hal/tutorial.html) was very enlightening. It introduces `halshow` and `halscope`, both of which are crucial tools for troubleshooting.

### [Ethercat installation from repositories - how to step by step)(https://forum.linuxcnc.org/ethercat/45336-ethercat-installation-from-repositories-how-to-step-by-step)

Rodw has an excellent post that details how to configure `linuxcnc-ethercat` for use with LinuxCNC. His post covers the basic installation required to get going. Read it and follow it step-by-step.

## Required Reading Part 2

### [Ethercat 64 bit stepper drive basic example EL7041](https://forum.linuxcnc.org/27-driver-boards/35717-ethercat-64-bit-stepper-drive-basic-example-el7041#319333)

This one can wait for later as it's more advanced, but I was able to take the example provided by Grotius and finally get an EL7041 to work for me. 

