# victron-tibber-ess-control

Charging and discharging of the battery on the basis of a dynamic electricity tariff, taking into account conversion losses and the expected solar yield. 

## Configuration

What needs to be configured?

Configuration nodes
* config-vrm-api
* pushbullet-config
* tibber-api-endpoint

Global settings node
* VRM Site ID
* VRM access token
* Battery capacity
* Price per kwh for solar power
* Efficiency of the inverter (conversion losses)
* Efficiency of the charger (conversion losses)
* Storage costs per kwh (wear and tear on the battery)

Stats: vrm_pv_charger_yield_fc node
* VRM Site ID

Stats: vrm_pv_inverter_yield_fc node
* VRM Site ID

## Hints

The flow uses the hourly Tibber prices to determine the best possible time to charge the battery. 
In addition, the expected solar surplus, calculated from the predicted solar yield and predicted consumption, is also taken into account.

To charge the battery, the "SOC minimum discharge value" is set to the top or the ESS mode "Keep batteries charged" is set.

Discharging the battery is only permitted if this makes sense, taking into account conversion losses (inverter and charger). 
The predefined values of 0.90 and 0.92 are valid for Multiplus 48/3000 and 48/5000.

Everyone must decide for themselves whether storage costs should be included or not. 
The battery is already there anyway and will probably die of old age sooner than of wear and tear.