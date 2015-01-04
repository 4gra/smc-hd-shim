Don't follow if you're not confident you can validate the results yourself:

  * Obtain ```smc```; build and install it.
  * Place the ```fanspeed``` executable in ```/usr/local/bin/```.
  * Test its operation with ```/usr/local/bin/fanspeed info```
  * Install the launchctl plist into ```/Library/LaunchDaemons/```
  * Start with:
     # launchctl load -w <path to plist>
     # launchctl start io.github.4gra.fanspeed
