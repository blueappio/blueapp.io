# BlueApp.io

Coming from the platform that helps you manage and track devices, this library enables developers to create apps for web and mobile using web bluetooth api. You can use this library to create apps for the Blueapp platform or for your personal bluetooth needs.

### Installation

There are three ways to integrate the library into your application.

Add the following line to your index.html

```
<script src="https://blueappio.github.io/blueapp.io/blueapp.io.min.js"></script>
```

Install via bower:

```
bower install blueapp.io --save
```

Install via npm:

```
npm install blueapp.io --save
```
Blueapp.io Web Bluetooth API is based on [Web Bluetooth Specifications](https://www.w3.org/community/web-bluetooth/), and it is supporting most of the features described here. You can check current [implementation status]().

### Web Bluetooth API Supported:

#### Device discovery
Feature                                 |   Supported functions | 
-----------------------------------     |   :------------: |
requestDevice()                           |   navigator.bluetooth.requestDevice(options)      |
Options should be object with either filers passed or acceptAllDevices set to true. In addition we can pass optionalServices - array of services we want to be available from the device (beside services in matched filter).
Supported filters:
 * name
 * namePrefix
 * services
 * manufacturerData
 * serviceData (basic support)


### Scanning
Feature                                 |   Supported functions | 
-----------------------------------     |   :------------: |
|  requestLEScan() |   navigator.bluetooth.requestLEScan(options)      |

Options - object of filter (same as requestDevice), keepRepeatedDevices (keep showing adverisement from same device), acceptAllAdvertisements (either this should be true or filters passed).
### BluetoothDevice
Bluetooth device object retured in promise from requestDevice(). Available functions:
 Supported functions | Description |
  :------------: |:--------------|
watchAdvertisement() | listening for advertisement of devices found |
unwatchAdvertisement() | stops listening for advertisement|
gatt.connect() | connecting to the device from gattServer|
watchAdvertisement() | listening for advertisement of devices found|
unwatchAdvertisement() | stops listening for advertisement|

### Server
Server object returned in promise from gatt.connect(). Available functions:
 Supported functions | Description |
  :------------: |:--------------|
getPrimaryService(uuid) | promise returns passed service from server if available |

### Service
Service object returned in promise from getPrimaryService(). Abaliable functions:
 Supported functions | Description |
  :------------: |:--------------|
getCharacteristic(uuid) | promise returns passed characteristic from service if available |
getCharacteristics(uuids) | promise returns array from passed characteristics from service if available |

### Characteristic
Characteristic object returned in promise from getCharacteristic(). Avaliable functions:
 Supported functions | Description |
  :------------: |:--------------|
getDescriptor(uuid) |  promise returns passed descriptor from characteristic if available |
getDescriptors(uuids) | promise returns array of passed descriptors from characteristic if available |
readValue() | promise returns DataView containing the data |
writeValue() | Bytes to be written Uint8Array |
startNotifications() | start notifying for value changes | 
stopNotifications() |  stop notifying for value changes | 

### Descriptor
Descriptor object returned in promise from getDescriptor(). Available functions:
 Supported functions | Description |
  :------------: |:--------------|
readValue() | promise returns DataView containing the data |
writeValue() | Bytes to be written Uint8Array |

### Events

 Supported events | fired on |
  :------------: |:--------------|
advertisementreceived                 |   BluetoothDevice object     |
gattserverdisconnected                |   BluetoothDevice object     |
characteristicvaluechanged            |   Characteristic object      |

For more more details check [getting started]() page.

### Extra Material

Follow Web Bluetooth Specification to build your Bluetooth App. [Click here for more info on Web Bluetooth](https://www.w3.org/community/web-bluetooth/)

Go to [BlueApp.io](https://www.blueapp.io) create an account, add the link to your application. 
Go to Organization->(Click your organization name)->My Applications

Note: You can use [Github Pages](https://pages.github.com/) to host your application.

[Check the other repos for more examples.](https://github.com/blueappio)