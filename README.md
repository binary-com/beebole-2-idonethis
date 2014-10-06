beebole-2-idonethis
===================

Post **beebole.com** entries to **idonethis.com**
-----------------------------------------

This script will post existing task entries from the time-recording tool
[__BeeBole__](http://beebole.com "BeeBole Home Page")
to the workgroup notification tool
[__iDoneThis__](http://idonethis.com "iDoneThis Home Page").

It uses the APIs of the respective products, described in the
[iDoneThis API Documentation](http://idonethis.com/api/v0.1/)
and the
[BeeBole API Documentation](http://beebole.com/api/).

Strategy
--------
In our organisation, __BeeBole__ records are stored as finely structured data
whereas __iDoneThis__ posts are usually just narratives; so it made sense to synchronize in that direction.
So this script will format a simple report out of the task comments and hours already posted to __BeeBole__, and
post that report to __iDoneThis__.

To authenticate yourself to each API you will first need to find your personal authentication tokens.
For both services, login using your usual account, and then you'll find your tokens here:

- [http://beebole.com/api/#authentication](http://beebole.com/api/#authentication)
- [https://idonethis.com/api/get_token](https://idonethis.com/api/get_token)

In each case the token is a string that looks typically like this: 

66767f3330876e1332ababa12345678ac20fa3b6

Cut-and-paste this and either set up environment variables as shown below or just patch the script.

Requirements
------------

- A valid account at __iDoneThis__
- A valid account at __BeeBole__
- A Linux terminal window
- curl (you almost certainly have this)

Instructions
------------

- Download [bbl2idt.sh](../blob/bbl2idt.sh) and put it anywhere
- chmod +x bbl2idt.sh
- Either:
  - Set up regular environment variables `BBL_TOKEN` and `IDT_TOKEN` to the values you retrieved above.
    The most convenient place to do this is in your .profile or .bash_profile.  e.g.: 


```bash
export BBL_TOKEN=66767f3330876e1332ababa12345678ac20fa3b6
export IDT_TOKEN=aba12345678ac20fa3b666767f3330876e1332ab
```

    After your next fresh login test that these are now available:

```bash
echo BBL_TOKEN is $BBL_TOKEN
echo IDT_TOKEN is $IDT_TOKEN
```

  - Alternatively, just hard-code your tokens as can be seen in the first few lines of the script.  It's not a sin.

Usage
-----

```
./bbl2idt.sh [yyyy-mm-dd]
```

This will do the synch for the given date.  The date is optional and defaults to today.

Author
------

Frank Carnovale

http://binary.com

