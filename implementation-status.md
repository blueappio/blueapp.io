# Blueapp.io Web Bluetooth implementation status


## Web Bluetooth features

Feature                                 |   Support status | 
-----------------------------------     |   :------------: |
requestDevice                           |   supported      |
getAvailability()                       |   supported      |
Referring Device (Physical Web)         |   not supported  |
Discovery                               |   supported      |
Available filters:                      |                  |
> services                              |   supported      | 
> name                                  |   supported      | 
> namePrefix                            |   supported      |
> manufacturerData                      |   supported      |
> serviceData                           |   basic support  |
> acceptAllDevices                      |   supported      | 
chooser UI                              |   supported      |
permissions.request()                   |   not supported  | 
permissions.query()                     |   not supported  |
permissions.revoke()                    |   not supported  |
BluetoothDevice                         |                  | 
> watchAdvertisements()                 |   supported      | 
> unwatchAdvertisements()               |   supported      | 
BluetoothRemoteGATTServer               |                  |
> connect()                             |   supported      |
> disconnect()                          |   supported      |
>  getPrimaryService()                  |   supported      |
> getPrimaryServices()                  |   supported      |
BluetoothRemoteGATTService              |                  |
> getCharacteristic()                   |   supported      |
> getCharacteristics()                  |   supported      |
> getIncludedService()                  |   not supported  |
> getIncludedServices()                 |   not supported  |
BluetoothRemoteGATTCharacteristic       |                  |
> getDescriptor()                       |   supported      |
> getDescriptors()                      |   supported      |
> readValue()                           |   supported      |
> writeValue()                          |   supported      |
> startNotifications()                  |   supported      |
> stopNotifications()                   |   supported      |
> characteristic Properties             |   supported      |
BluetoothRemoteGATTDescriptor           |                  |
> readValue()                           |   supported      |
> writeValue()                          |   supported      |
Events                                  |                  |
> advertisementreceived                 |   supported      |
> availabilitychanged                   |   not supported  |
> characteristicvaluechanged            |   supported      |
> gattserverdisconnected                |   supported      |
> serviceadded                          |   not supported  |
> servicechanged                        |   not supported  |
> serviceremoved                        |   not supported  |
BluetoothUUID                           |   supported      | 
TypeError for bad filters               |   supported      | 


## Web Bluetooth Scanning

Feature                                 |   Support status |
--------------------------------------- |   :------------: |
requestLEScan                           |   supported      |
Available filters:                      |                  |
> services                              |   supported      | 
> name                                  |   supported      | 
> namePrefix                            |   supported      |
> manufacturerData                      |   supported      |
> serviceData                           |   basic support  |
> keepRepeatedDevices                   |   supported      | 
> acceptAllAdvertisements               |   supported      | 
Events                                  |                  |
> advertisementreceived                 |   supported      |
BluetoothLEScanPermissionDescriptor     |   not supported  |
BluetoothLEScanPermissionResult         |   not supported  |