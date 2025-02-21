# Stepper Motor Tutorial

_note: I'm still learning LinuxCNC and motor tuning, but I'm hoping this will get you off the ground in less time than I took_

Hopefully this tutorial will help you get set up using a Beckhoff EL7041 stepper driver.

![example stepper motor setup](./img/stepper-setup.jpg)

## Overview
* [Hardware Overview](#hardware-overview)
* [Required Reading](#required-reading)
* [Stepper Motor Example](#stepper-motor-example)

## Hardware Overview
* [EK1100 | EtherCAT Coupler](https://www.beckhoff.com/en-us/products/i-o/ethercat-terminals/ek1xxx-bk1xx0-ethercat-coupler/ek1100.html)
    * The EK1100 copules an ethernet connection with the EtherCAT devices
* [EL7041 | EtherCAT Terminal, 1-channel motion interface, stepper motor, 48 V DC, 5 A, with incremental encoder
](https://www.beckhoff.com/en-us/products/i-o/ethercat-terminals/el-elm7xxx-compact-drive-technology/el7041.html)
![el7041-pin and led layout](./img/el7041-layout.png)
* Some flavor of stepper motor and and encoder
    * I'll be using an [AS2022 | Stepper motor, holding torque 1.50 Nm, N2 (NEMA23/56 mm)
    ](https://www.beckhoff.com/en-us/products/motion/compact-drive-technology/asxxxx-stepper-motors/as2022.html) but I'll also demonstrate with a [Nema 17 Stepper](https://www.amazon.com/dp/B00W98YK5M) and [rotary encoder](https://www.amazon.com/dp/B01EWK933S) from Amazon. 


## Required Reading

### [Basic Digital Outputs](../basic_digital_outputs/readme.md)

The basic EtherCAT example in this repo should help you get off the ground. Once you grok that come back and let's move forward with steppers.

### [Ethercat 64 bit stepper drive basic example EL7041](https://forum.linuxcnc.org/27-driver-boards/35717-ethercat-64-bit-stepper-drive-basic-example-el7041#319333)

LinuxCNC forum user Grotius posted an excellent example and we'll mostly be working from it, but hopefully with more detailed explanations


### [LinuxCNC Ethercat Docs - EL7041](https://linuxcnc-ethercat.github.io/linuxcnc-ethercat/el7041.html)
This page demonstrates ways to configure the EL7041 modules directly from the XML.

## Stepper Motor Example

Let's build an axis in LinuxCNC!

### `el7041-conf.xml`
Let's start by creating our `el7041-conf.xml` file:
```xml
<masters>
  <master idx="0" appTimePeriod="100000" refClockSyncCycles="5">
    <slave idx="0" type="EK1100" />
    <slave idx="1" type="EL7041" name="x-axis">
		<modParam name="maxCurrent" value="2" />
		<modParam name="nominalVoltage" value="24.0" />
	</slave>
  </master>
</masters>
```

From our [last example](../basic_digital_outputs/basics/ethercat-config.xml) you'll notice a couple changes. 

The first being that one of our slaves has an additional attribute `name`. This attribute gives us a convenient way of referring to this axis. Recall that [in the past](../basic_digital_outputs/readme.md) we used the `setp` command in `halrun` to set parameters, i.e. `setp lcec.0.1.dout-0 1` (where we turned on channel 0 of master `0`s slave `1`). By utilizing the `name` attribute in the XML we can give our slave a name `x-axis` and refer to it in `halrun` via `lcec.0.x-axis` for all of our HAL configurations. 

The second being that we're utilizing the `modParam` elements of the slaves. You should recall from the [LinuxCNC Ethercat Docs - EL7041](https://linuxcnc-ethercat.github.io/linuxcnc-ethercat/el7041.html) that the EL7041 driver exposes a suite of additional parameters (varying by exact model). In our example there are two that really matter.
* The first being the `maxCurrent` that we're allowing through our motor. My AS2022 accepts up to 5.6A, but my tiny Nema 17 can only handle 1.68A, so this setting will vary by motor. 
* The second being the `nominalVoltage` that the EL7041 shoudl expect. The EL7041 accepts a separate motor power supply on pins 4\` and 8\` and you'll want to make sure your `nominalVoltage` parameter matches the voltage provided.
    * If this doesn't match you'll see warning LED illuminated the flag `srv-warning` set. (in this example case the full path would be `lcec.0.x-axis.srv-warning`)

### `el7041.hal` and `mill.ini`

These two files are deeply intertwined and I won't pretend to know everything about them. I will do my best to comment them with links to documentation so that as you go through them you can easily look up what is doing what. I've stripped the `.ini` file down to what I believe is the minimum required for the example; there are MANY more [configuration settings available](https://linuxcnc.org/docs/html/config/ini-config.html) and it would do you well to learn about them.
