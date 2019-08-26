# PID Logic with Boil and Pump control

## Mash and boil in single vessel

If the target Temperature is above a configurable `Max. PID Temperature` threshold the PID will be ignored and heater is switched into boil mode. This is helpful if you use the same kettle for mashing and boiling.

In boil mode, the heater will be constantly on until the target Temperature is above a configurable `Max. Boil Temperature` threshold where the power will be reduced to the `Max. Boil Output`. This is helpful to reduce power usage, avoid scorching and reduce boil overs.

## Automatic Pump Control

While not in boil mode the pump will be run for `Mash Pump Rest Interval` seconds, then switched off for `Mash Pump Rest Time` seconds, and then the cycle will repeat.

While in boil mode the automatic pump control is disabled allowing for manual control of the pump (e.g. to sanitize a plate-chiller or counterflow chiller)

## Parameters

* `P` - proportional value
* `I` - integral value
* `D` - derivative value
* `Max. Output` - Max power for PID and Ramp up.
* `Max. PID Temperature` - If Target Temperature is set above this, PID will be disabled and Boil Mode will turn on.
* `Max. Boil Output` - Heater power when Max Boil Temperature is reached.
* `Max. Boil Temperature` - When Temperature reaches this, power will be reduced to Max Boil Output.
* `Internal Loop Time` - In seconds, how quickly the internal loop will run, dictates maximum PID resolution (e.g. 0.1). The lower the more accurate but more demanding on your Pi. You should also consider how fast your relays etc can switch when setting this.
* `Mash Pump Rest Interval` - In seconds, how long the pump will run during mash phase before resting.
* `Mash Pump Rest Time` - How long the pump will be off during the rest interval