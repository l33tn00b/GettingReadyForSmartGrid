# Preface
Getting ready for Smart Grid Integration

This is to document how I'm grappling with Smart Grid Integration.

# Equipment
I'd love to integrate

- Chinese Solar Generator with approx. 10 kWp,
- Chinese Battery having a capacity of 20 kWh,
- German Electric Vehicle with approx. capacity of 40 kWh,
- German Heat Pump, 2..4 kW.

All the stuff is networked and has various - incompatible, of course - APIs.


# What I've tried...

## evcc for automated vehicle charging when having surplus energy
Upsides:
- Works with the solar generator and battery (Modbus TCP local network API) .
- Works with the car (Manufacturer Web API)
- Initially worked with the wallbox (local network https API).

Long story short: It sucks. 
- First, they broke my wallbox integration by pushing an update that made sponsorship mandatory for my type of wallbox. 
- Then, there's that "my way or the highway" philosophy. There is no way of manually starting a charge (i.e. via the wallbox app or an RFID card). That's a no-go for my significant other...  Some ideas die fast.

So I threw that one out. Next idea for surplus charging is hacking a solution with my home automation server.

