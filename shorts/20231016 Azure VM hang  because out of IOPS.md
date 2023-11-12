## Problem
  I used a azure ubuntu to deploy an Nodejs Application (migrated from google cloud). My application consumed ~ 120 IOPS. Everything going fine til one day: 
  - The application hang, not response anymore from health check endpoint.
  - ssh connection to VM is very slow

I found that all the bursted IOPS was consumed. The IOPS grahp show that system going too hight for IOPS. After few days of monitoring, I found that:

## What I learned
 - The IOPS is very high at 3PM every day. => There is timer that check and daily update for the VM. You could show all the timers running by:
```
sudo systemctl list-timers
```

I found that there are some timers running at that time to update the system. I feel that something could be wrong with the system update. So I try to disable the those timers (Not recommended), I would like to manual update the VM myself, to avoid the out of IO issue.

```
sudo systemctl stop apt-daily-upgrade.timer
sudo systemctl disable apt-daily-upgrade.timer
systemctl stop apt-daily.timer
sudo systemctl disable apt-daily.timer
```

Few days later the IOPS is still not stable. The IOPS very high if the sqlite file about 200MB. I checked around, seem the OS having some issue when disrupting the OS upgrade last time (From 20 -> 22 LTS). 
I decided to create new machine with fresh latest LTS os. 

## Results
The IOPS is stable, and the system is not hang anymore. I could ssh to the VM without any issue.
