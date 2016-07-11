# BlueApp.io
Simple library to connect Bluetooth devices.

There are two ways to integrate the library into your application,

Add the following line to your index.thml
```
<script src="https://blueappio.github.io/blueapp.io/blueapp.io.min.js"></script>
```

Or, install it via bower
```
bower install blueapp.io --save
```

Follow Web Bluetooth Specification to build your Bluetooth App. [Click here for more info on Web Bluetooth](https://www.w3.org/community/web-bluetooth/)

Go to [BlueApp.io](https://www.blueapp.io) create an account, add the link to your application. 
Go to Organization->(Click your organization name)->My Applications

Note: You can use [Github Pages](https://pages.github.com/) to host your application.

[Check the other repos for more examples.](https://github.com/blueappio)

### Web Bluetooth API Support:

|API Method/Property/Eevent  | Remarks
|----------|------------
| navigator.bluetooth.requestDevice() | Filters are ignored. Filters are applied in BluAapp.
| device.gatt.connect() | Attempts to connect internally up to three times
| server.getPrimaryService() |
| service.uuid |
| service.getCharacteristic() |
| characteristic.uuid |
| characteristic.service |
| characteristic.properties | Supported: broadcast, read,  writeWithoutResponse, write, notify and indicate
| characteristic.getDescriptor() |
| characteristic 'oncharacteristicvaluechanged' event |
| characteristic.readValue() |
| characteristic.writeValue() |
| descriptor.uuid |
| descriptor.characteristic |
| descriptor.readValue() |
| descriptor.writeValue() |
