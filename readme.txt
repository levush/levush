Lightweight Embedded Versatile User Shell 
is a shell to be run on unixoid systems. 
Levush will use Libcli to provide a Ci$co-like command-line interface
for unixoid systems.
So there will be a levush for different targets like
-openwrt (uci is first, as luci is too big) 
-OpenBSD (will be cool to have a secure router like os)
-debian linux. (maybe)
License will be BSD for the start but I am not sure if I change it to GPL3
or make a dual license BSD/GPL3 if this is possible.

The first target will be openwrt because openwrt is a nice os to be run on old
 plastic routers. Unfortunately, the openwrt project decided not to support 
small routers with only 4M flash anymore.
As there are many such routers and as the luci web gui using lua scripts takes 
a lot of flash I thought it would be nice to have a router cli "for real men"
 that mimics a $router-os like like cli with some funny extensions to get a 
shell or to execute other commands like upgrading openwrt or adding software.

The idea is to just use ssh, theoretically one can use telnet, but nobody likes 
telnet, really.
The router will have a user called admin in /etc/passwd that has /sbin/levush 
as his shell. So when the user logs in she gets the $router-os like levush. 

As libcli and uci of opernwrt are written in c levush is also plain c and it is 
not expandable by config files or the like. The functions of levush are 
hardcoded into levush and levush can be statically linked so it just runs 
and does what it is made for, administer the router in a very secure and 
reliable way. 
So for openwrt levush will use UCI which stands for Unified Configuration 
Interface, and it may be necessary to configure and build a new levush 
for a router if it has very different features. We will see.
In principle levush is stupid and holds no own config files it just knows
how to parse existing config files and how to present the content to the user.
If the user uses the config mode to change settings, levush will understand
the settings and check them for correctness (syntax) and will edit the
/etc/config uci files in case of an openwrt router.
So if one enters:
router> show vlan
levush will read /etc/config/network and display the configured vlans.

The look and feel shall be that of a "professional" router.
So admins who know how to administer big routers will feel at home and 
people not knowing to administer big routers can use levush as a playground
to learn the basics.

So hopefully I have enough time to write levush for an 19.x openwrt router
which will be the first target as uci is so well structured and because
luci is too fat for a 4M flash router.

Levush, Sat Dec 21 14:10:32 EST 2019

