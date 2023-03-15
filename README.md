# Preface
Getting ready for Smart Grid Integration

This is to document how I'm grappling with Smart Grid Integration.

# Equipment
I'd love to integrate

- Chinese Solar Generator with approx. 10 kWp,
- Chinese Battery having a capacity of 20 kWh,
- Austrian Wallbox capable of 22kW charging,
- German Electric Vehicle with approx. capacity of 40 kWh,
- Not-So-German Heat Pump (normally 2..4 kW, with additional electrical heating of 12kW).

All the stuff is networked and has various - incompatible, of course - APIs.

# Totally unfounded observations
- Our grid sucks. There's worse but there's also much better. Why? Some time ago EU regulations degraded grid capacity: In the 70s there were massive capacities for residential areas (nuclear power, everybody had electrical heating). Then, EU regulations downgraded the minimum standard (and no one wanted to pay for more than the (newly set) bare minimum). So we now have residential areas which are unfit for large electrical loads (think EV, heat pump,...). I'm happy to live in a house having 3x50 Amps breakers only to have these downgraded to 35 Amps). Finger to you! And a big finger to our officials unable to rectify this mess, instead trying to push electrification while at the same time talking about forced limiting of consumption. 
- Could someone please fix this mess of incompatible APIs and standards? EU? See above...
-

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

## Getting Pricing Data for variable electricity tariffs.
There's two large consumers (car and heat pump). These loads can be shifted to off-peak times when electricity is much cheaper. That makes having a variable electricity tariff quite logical. Additionally, there's the battery which can be charged when electricity is cheap. but first, we need to get a feel for it. So we need data... Theres different tariffs but all are based on day ahead traded electricity. So we need to access that data. Multiple possible solutions to get data from
- Spot Market exchange (EPEX)
- directly from electricity company (Tibber / Awattar)
- EU Transparency Platform.

### EPEX Spot Market
- https://www.epexspot.com/en/market-data?market_area=DE-LU&trading_date=2023-03-14&delivery_date=2023-03-15&underlying_year=&modality=Auction&sub_modality=DayAhead&technology=&product=60&data_mode=table&period=&production_period=
- -Limited Data available (no history)
- -No (free) download
- -Requires web scraping
- +chart available

### Awattar
Haven't tried for current data yet because they stopped offering to new customers.
But one can download historical pricing data via their Web API.
Figuring out the final price is tricky because it doesn't get displayed (only Spot Market Price).

### Tibber
- -Limited Data available (next day doesn't work)
- +All inclusive pricing displayed
- +Better chart than EPEX
- -Web Scraping required to extract data.

### ENTSO-E (EU Transparency Platform)
- 
