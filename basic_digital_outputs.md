# Basic Digital Outputs Example

Alright, so you've read a little bit about how HAL works, but you're trying to figure out the next steps to actually make an LED blink. This example should give you enough tools to create a blinking LED version of a "hello world" program.

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

## Basic Digital Outputs
