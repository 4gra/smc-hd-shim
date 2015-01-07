Don't follow if you're not confident you can validate the results yourself:

  * Obtain ```smc```; build and install it.
  * Place the ```fanspeed``` executable in ```/usr/local/bin/```.
  * Test its operation with ```/usr/local/bin/fanspeed info```
  * Install the launchctl plist into ```/Library/LaunchDaemons/```
  * Start / autostart with: ```launchctl load -w <path to plist>; launchctl start io.github.4gra.fanspeed```
  * Make sure it's changing the fan speed appropriately with further calls to ```/usr/local/bin/fanspeed info```.

Optional unit tests, if you like that sort of thing and use roundup:
  * run tests/fanspeed.rup in situ (before installing)
  * run tests/installed.rup as root once installed.
