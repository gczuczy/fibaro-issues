# MTU Problems

If you are having an internet connection which has a lower MTU than 1500 (typical for pppoe), then since around 2020-04 both HC2 and HC3s won't be able to communicate properly. Small packages (payload smaller than 1452) will work, anything above will not.

# Workarounds

I've found two workarounds.

First one is to route the home center through a VPN connection which provides a full 1500 MTU on the whole path. This works for both HC2 and HC3, however it's a very technical solution, not many having the ability to do this.

The second one, which is more elegant is to set the interface-mtu DHCP option for the HC to 1492. Unfortunately the HC2 ignores this option, so it only works for the HC3.

