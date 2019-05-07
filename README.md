# Launch Synergy Client headlessly
Somehow Synergy GUI doesn't play well with `Pop!_OS` (based on Ubuntu 18.04), but both Synergy Server and Client can run headlessly.

Create following shell script, add execution permission and add to startup application.
```
##!/bin/bash
SYNERGY_SVR_ADDR=YOUR_SERVER_ADDRESS
synergyc --daemon --debug INFO $SYNERGY_SVR_ADDR
```
