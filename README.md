###

Prerequisite:
Install localtuya on HACS: https://github.com/rospogrigio/localtuya

###
###
###

We have to do some modifications on climate related python scripts to support the devices.
See localtuya_changed_files folder. You can copy paste these of course, but not sure if the version of localtuya by the time you try this will be compatible with the files under localtuya_changed_files.
---
const.py: Added these 2 lines under Climate region:
CONF_IS_ELKO = "is_elko"
CONF_IS_ELKO_BATHROOM = "is_elko_bathroom"
---
strings.json: Added these 2 lines:
"is_elko": "Is ELKO",
"is_elko_bathroom": "Is ELKO and for bathroom"
---
translations: Each json file: Same changes with strings.json. Added just 2 lines related to is_elko, is_elko_bathroom.
---
climate.py:
Many changes. Search "#ELKO" and you will see the modifications.

###
###
###

How to add devices - steps:
First Screen:
	Put "device name" below in "Name"
	Local key from below too.
	Protocol Version: 3.3
	Enable Debug
	Next.
Second Screen:
	Put any string in "Friendly Name"
	Set Target Temperature and Current Temperature based on matters below.
	Temperature Step: For bathroom: 1, for others 0.5
	Leave max and min temperatures blank
	Precision: 0.1
	HVAC Mode DP: 140
	HVAC Mode Set: Manual/Auto
	Leave Current Action DP, Action Set, ECO DP, ECO Value, Presets DP blank
	Temperature Unit: Celsius
	Target Precision 0.1
	Check "Is ELKO"
	NOTE: You must check "Is ELKO and for bathroom" during "Add Device" (first registration of device). Save it, then edit the device and uncheck, save.

###
###
###


Normal Heaters:
____________________
Target: dp 107
Current: dp 104
Set off: dp 116 to true, 107 to 0

Bathroom Heaters:
____________________
Target: dp 107
Current: dp 109
Set off: dp 116 to true, 107 to 0

###
###
###

---------------------------
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
---------------------------
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
--------------------------- 
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
--------------------------- 
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
--------------------------- 
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
--------------------------- 
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
--------------------------- 
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX
--------------------------- 
device name:    XXXXXXXXXXXXXX
device id:      XXXXXXXXXXXXXX
local key:      XXXXXXXXXXXXXX

###
###
###

How to get these local keys?
____________________
Fetch this: https://github.com/FlagX/ha-ledvance-tuya-resync-localkey/tree/main
Under ha-ledvance-tuya-resync-localkey/pyscript_modules/tuya/const.py change TUYA_CLIENT_ID and TUYA_SECRET_KEY with:
---
ClientID: yrtjvgv7umgpgdf5efcj
Secret: A_vxts9r5kn3ys45t4npqhvjrdy87qnnht_83fnh4gakypwnqrwfurc7pst9sqpfxat
Note: It was a hell to obtain these. Android emulator, frida-tools, apktool etc. a lot of reverse engineering had to be done. See this: https://blog.rgsilva.com/reverse-engineering-positivos-smart-home-app/
---
Then run print-local-keys.py