smc-hd-shim
===========
Ersatz fan speed control for Macs with unsupported hard drives.
Makes use of the
[smc](https://github.com/hholtmann/smcFanControl/tree/master/smc-command) tool
for all low-level stuff.

WARNING!
========
Don't use this tool unless you're content you can manage the consequences of it
doing the wrong thing or failing completely, and your Mac overheating and
destroying data, curtains, cities, etc. (I wrote this for my own laptop and am
reasonably confident I'll know it's failed as I'll hear it, or feel my legs
cooking).

Purpose
=======
Sets a fan speed appropriate to the Mac CPU temperature at any given moment.  I
needed this following installation of a ```ST500LM000``` in my MacBook Pro,
which caused both fans to revert to a 'safe mode' ~6000RPM in the absence of
Apple HD firmware-provided temperature data.  I gather I'm not alone and
similar problems have been reported against some models of iMac so asume this
might be of wider use while there are still Macs with replaceable components.

Limitations
===========
Only checks key  ```Th0H```!  This thermal input may not even exist on your
hardware.  Use the ```smc``` tool to check this assumption.  Doesn't take any
other thermal input into account, and doesn't check HDD SMART info either.

The decision to work off one input was checked carefully on my laptop at the
time, and it seems to have worked perfectly well on *my* MacBookPro4,1.  In
adapting this for your hardware you should take into account your specific
hardware (and even upgrades, potentially).

That said, it's never to my knowledge failed (thanks to launchd I assume) and
contains a few basic sanity checks to prevent terrible behaviour.

Things to Tweak
===============
All these are simple to change.

In the provided launchctl plist:
   * time between updates

In the agent script:
   * hard-coded min/max fan values ```min```, ```max```
   * temperature/speed curve
   * keys of fans to control

Suggested Improvements
======================
   * Multiple inputs (including SMART) controlling fans separately for a
     slightly quieter / more controlled system
   * Rewrite all in C based on ```smc``` code
   * Better logging
   * Locking
