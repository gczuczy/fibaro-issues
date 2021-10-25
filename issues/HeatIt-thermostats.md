# Problem description

Only affects HC3.

Heatit provides very nice thermostats for usecases what the fibaro products not even remotely are covering. Best example is thermostats for underfloor heating with floor sensors. The problem comes when the central heater needs to be turned on when any of the thermostats require heating.

The thermostat state is present in the system, displayed on the HC3, however you are unable to trigger on it using block scenes - it's simply not offered in the dialogs.

In fibaro's opinion you should be using the thermostat's mode, which actually disables the thermostats. This means, fibaro tells you to run around the house periodically, check what room is not warm enough, and turn your thermostat on, if you need heating in that zone (lol).

# Workaround

The thermostat state is present in the system, and with API scraping, you can get it out. This means you are able to use it in LUA scenes. So, this actually works, but if you have a fair amount of thermostats, maintaining the triggers will be very hard, because fibaro parses and dumps your conditions, instead of saving it. This means, you can't build on tirival things like comments or ordering, or anything similar.

Here's how you can trigger on it:
```
{
  conditions = { {
    id = 918,
    isTrigger = true,
    operator = "==",
    property = "thermostatOperatingState",
    type = "device",
    value = "Heat"
  } },
  operator = "all"
}
```

The value changes between "Idle" and "Heat", so these has to be used in the triggers.
