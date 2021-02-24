hdhomerun-vlc
=============

Simple Bash script to tune my HD Homerun to a station of my choice, and open the stream in VLC.

Requires the hdhomerun_config binary on your path.
Requires VLC is installed.
Only used/tested on OS X.

Currently contains my channel map hard-coded.  I may or may not ever improve on this.  This script was written to make my life a little easier.

I expanded on this because Plex has been failing me the past year trying to stream from my HD-HOMERUN. So far this method is solid versus the Plex gamble on whether it will work or not.

> New things: 
> . Now tested on Linux ( Ubuntu 20.04 LTS ).
> . Removed the hardcoded channel menu but the case statement now parses config files.
> . Added a while loop to look for vlc process and when you cloase vlc it sets both tuners back to none.


If you use the hdhomerun_config to run a channel scan and output to scan0.log run the below

`cat scan0.log | grep -B 2 -v "LOCK: none" | egrep "seq=100|PROGRAM|SCANN" | egrep -B 1 "LOCK|PROGRAM" | sed -e '/^--$/d'`

This will only narrow down the real channels and then you can further modify into the below tunerX.cfg files.

Script looks at tunerX.cfg as I have a HDHR-US model that has dual antenna inputs. The layouts are CHANNEL:PROGRAM:DESCRIPTION

> $HOME/.tvcfg/tuner0.cfg
> 35:3:66.1 ION
> 35:4:66.2 qubo
> 35:5:66.3 IONPlus
> 35:6:66.4 Shop
> 35:7:66.5 HSN

> $HOME/.tvcfg/tuner1.cfg
> 36:3:5.1 WTTG-DT
> 36:4:20.1 WDCA
> 36:5:5.2 BUZZR
> 36:6:5.3 ME TV
> 36:7:20.2 MOVIES


