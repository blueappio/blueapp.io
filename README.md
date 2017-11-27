# BlueApp.io

Blueapp.io is fast, easy to use and feature-rich Web Bluetooth library. It is based on Web Bluetooth spec, and enables developers to create apps for web and mobile for discovering, connecting, and listening for advertisement of bluetooth devices. You can use this library to create apps for the Blueapp platform or for your personal bluetooth needs.

To get started, check out [instructions](https://github.com/blueappio/blueapp.io/blob/gh-pages/getting-started.md) page.

To look at the current feature support, and comparison between different platforms check [implementation status](https://github.com/blueappio/blueapp.io/blob/gh-pages/implementation-status.md) page.

## Quick start

* Add source to index.html:
```
<script src="https://blueappio.github.io/blueapp.io/blueapp.io.min.js"></script>
```

* Install via bower:
```
bower install blueapp.io --save
```

* Install via npm:
```
npm install blueapp.io --save
```


## Quick Overview:


#### Device discovery
|   Feature                                 |   Supported functions | 
|   :-----------------------------------    |   :------------ |
|    requestDevice()                        |   navigator.bluetooth.requestDevice(options)      |


#### Scanning
|  Feature                                 |   Supported functions | 
|  :-----------------------------------     |   :------------ |
|  requestLEScan() |   navigator.bluetooth.requestLEScan(options)      |

#### BluetoothDevice
Bluetooth device object retured in promise from requestDevice(). Available functions:

|  Supported functions | Description |
 |  :----------- |:--------------|
|  watchAdvertisement() | listening for advertisement of devices found  |
|  unwatchAdvertisement() | stops listening for advertisement  | 
|  gatt.connect() | connecting to the device from gattServer  |
|  watchAdvertisement() | listening for advertisement of devices found  |
|  unwatchAdvertisement() | stops listening for advertisement  |

#### Server
Server object returned in promise from gatt.connect(). Available functions:

 | Supported functions | Description |
 | :------------ |:--------------|
|  getPrimaryService(uuid) | promise returns passed service from server if available |

#### Service
Service object returned in promise from getPrimaryService(). Abaliable functions:

| Supported functions | Description |
| :------------ |:--------------|
| getCharacteristic(uuid) | promise returns passed characteristic from service if available |
| getCharacteristics(uuids) | promise returns array from passed characteristics from service if available |

#### Characteristic
Characteristic object returned in promise from getCharacteristic(). Avaliable functions:

| Supported functions | Description |
| :------------ |:--------------|
| getDescriptor(uuid) |  promise returns passed descriptor from characteristic if available |
| getDescriptors(uuids) | promise returns array of passed descriptors from characteristic if available |
| readValue() | promise returns DataView containing the data |
| writeValue() | Bytes to be written Uint8Array |
| startNotifications() | start notifying for value changes | 
| stopNotifications() |  stop notifying for value changes | 

#### Descriptor
Descriptor object returned in promise from getDescriptor(). Available functions:

| Supported functions | Description |
| :------------ |:--------------|
| readValue() | promise returns DataView containing the data |
| writeValue() | Bytes to be written Uint8Array |

#### Events

| Supported events | fired on |
| :------------ |:--------------|
| advertisementreceived                 |   BluetoothDevice object     |
| gattserverdisconnected                |   BluetoothDevice object     |
| characteristicvaluechanged            |   Characteristic object      |


#### Extra Material

[Check the other repos for examples.](https://github.com/blueappio)