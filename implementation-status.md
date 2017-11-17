# Blueapp.io Web Bluetooth implementation status


## Web Bluetooth features

Feature                                 |   Blueapp| Mac | Linux | Windows | 
-----------------------------------     |   :------------ | : --------	| :---------|:---------|
requestDevice                           |   ✅ |	 ✅ |	 ✅ |		 ✅ |
getAvailability()                       |   ❌ |		❌ |	❌ |	❌ |
Referring Device (Physical Web)         |   ❌ |		❌ |	❌ |		❌ |
Discovery                               |   ✅  |		✅ |		 ✅ |		✅ |
**Available filters: **                     |                  |				|		   |				|
└ services                              |   ✅ | 	✅ |		✅ |		✅ |
└ name                                  |   ✅ | ✅ |	✅ |		✅ |
└ namePrefix                            |   ✅  |		✅ |	✅ |	✅ |
└ manufacturerData                      |   ✅  |		❌		|		 ❌ |	❌		|
└ serviceData                           |   ☑️ partially  |		❌	|	❌   |	❌		|
└ acceptAllDevices                      |   ✅ | 			✅ 	|		✅    |			✅	|
chooser UI                              |   ✅ |		✅ 	|		✅  |	✅			|
permissions.request()                   |   ❌    | 	❌		|	❌   |		❌		|
permissions.query()                     |   ❌  |			❌	|		❌  |		❌		|
permissions.revoke()                    |   ❌   |		❌	|	❌	   |		❌ 		|
**BluetoothDevice**                    |                  | 				|		   |				|
└ watchAdvertisements()                 |   ✅ | 		❌		|		❌   |❌|
└ unwatchAdvertisements()               |   ✅ | 	❌			|		  ❌ |	❌			|
**BluetoothRemoteGATTServer**               |                  |				|		   |				|
└ connect()                             |   ✅ |			 ✅	|		 ✅   |			❌	|
└ disconnect()                          |   ✅  |			 ✅	|		 ✅   |		❌		|
└ getPrimaryService()                  |   ✅ |		✅		|	✅	   |		❌		|
└ getPrimaryServices()                  |   ✅ |	✅			|	✅	   |		❌		|
**BluetoothRemoteGATTService**              |                  |				|		   |		❌		|
└ getCharacteristic()                   |   ✅ |		✅		|		✅   |			❌	|
└ getCharacteristics()                  |   ✅ |		✅		|		✅   |		❌		|
└ getIncludedService()                  |   ❌     |		❌ 		|	❌ 	   |		❌		|
└ getIncludedServices()                 |   ❌ |		❌ 		|	❌ 	   |			❌	|
**BluetoothRemoteGATTCharacteristic**       |                  |				|		   |		❌		|
└ getDescriptor()                       |   ✅ |			✅	|		✅   |			❌	|
└ getDescriptors()                      |   ✅ |			✅	|		✅   |			❌	|
└ readValue()                           |   ✅ |			✅	|	✅	   |			❌	|
└ writeValue()                          |   ✅ |	✅			|	✅	   |			❌	|
└ startNotifications()                  |   ✅ |		✅	|		 ✅  |			❌	|
└ stopNotifications()                   |   ✅ |		✅		|	✅	   |			❌	|
└ characteristic Properties             |   ✅ |	✅			|	✅	   |			❌	|
**BluetoothRemoteGATTDescriptor**           |                  |				|		   |				❌|
└ readValue()                           |   ✅ |		✅		|	✅	   |			❌	|
└ writeValue()                          |   ✅ |	✅			|	✅	   |			❌	|
**Events**                                  |                  |				|		   |			❌	|
└ advertisementreceived                 |   ✅ |		❌		|	❌	   |			❌	|
└ availabilitychanged                   |   ❌ |			❌	|	❌	   |			❌	|
└ characteristicvaluechanged            |   ✅ |		✅		|		✅   |			❌	|
└ gattserverdisconnected                |   ✅ |		✅		|	✅	   |			❌	|
└ serviceadded                          |   ❌ |		❌		|	❌	   |			❌	|
└ servicechanged                        |   ❌     |		❌		|		❌   |			❌	|
└ serviceremoved                        |   ❌ |		❌		|	❌	   |			❌	|
BluetoothUUID                           |   ✅ | 		✅		|		✅   |			❌	|
TypeError for invalid filters               |   ✅ | 		✅		|	✅	   |			❌	|


----------

## Web Bluetooth Scanning

Feature                                 |   Blueapp | Mac | Linux | Windows | 
--------------------------------------- |   :-------- | :-----------|:------|:----------|
requestLEScan                           |   ✅ |	❌	|  ❌ |	❌	|
**Available filters:**                      |            |			|	   |		|
└ services                              |   ✅ | ❌	|		 ❌  |			❌	|
└ name                                  |   ✅ | 	❌	|		❌   |			❌	|
└ namePrefix                            |   ✅ |	❌	|		❌   |		❌		|
└ manufacturerData                      |   ✅ |	❌	|	❌	   |		❌		|
└ serviceData                           |   ☑️ partially  |		|		   |	❌	|
└ keepRepeatedDevices                   |   ✅ | 	❌	|	❌	  |		❌	|
└ acceptAllAdvertisements               |   ✅ | 	❌	|	❌	   |	❌	|
**Events**                                  |            |			|	  |			|
└ advertisementreceived                 |   ✅ |	❌	|	❌	   |			❌	|
BluetoothLEScanPermissionDescriptor     |   ❌ |	❌	|	❌	  |		❌|
BluetoothLEScanPermissionResult         |   ❌ |	❌		|	❌   |	❌	|