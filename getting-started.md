# BlueApp.io

## Overview
Coming from the platform that helps you manage and track devices, this library enables developers to create apps for web and mobile using web bluetooth api. You can use this library to create apps for the Blueapp platform or for your personal bluetooth needs.

## Blueapp.io management

First, in order to create new application for Blueapp platform, we need to login to [Blueapp.io](http://blueapp.io/). Selecting Organizations menu, we can open existing organization or we can create new one. Select organization and click on My Application tab. Clicking on plus sign we can add new application posting url, name and filter. Here you can also manage existing application, change their filter, url or description.

### Creating new application

First thing, before we start to write new javascript application, we have to import our Web Bluetooth blueapp.io library into our new project.

#### Installation

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


After adding blueapp.io library into your project, we should have bluetooth object available into navigator. Of course, in order to work with bluetooh devices we must have bluetooth adapter on platform that we are working on.

Since we have bluetooth in navigator, we have access to Web Bluetooth features such as requesting device or scanning. 

#### requestDevice()

When we call requestDevice on navigator.bluetooth we are first initiating scan from our bluetooth adaptor, and then matching scan results with passed parameters - mandatory Object that defines filters. As a parameter in requestDevice() function we should pass object with either filter or acceptAllDevices set as true. Additionally we can pass optionalServices - array of services we want to use from device. Filters should be array of objects and it can contain:
* name - the advertised the name of the device; often set by the manufacturer unless modified by the device user
* namePrefix - an initial substring of any length that matches an advertised device name
* services - an array including at least one service being advertised by the device 
* manufacturerData - object containing manufacurerData id and dataPrefix/mask of advertised data
* serviceData - object containing serviceData id
If we don't pass any of filters we should set acceptAllDevices to true. In that case, if we want to use any of device services, we have to pass services in optionalServices.

> **Note:**

> - Services are presented as 16 bit or 128 bit uuids. These uuids represent services uuids that are advertised by the bluetooth device. We can also provide name of the service from the list of [standardized Bluetooth GATT service](https://developer.bluetooth.org/gatt/services/Pages/ServicesHome.aspx)
> - Device should match one of the filters passed in filters array (in case we have more than one). In case we have, for example, name and services in one filter object, device must match both of them.
> - If we pass filters and acceptAllDevices, we should get typeError
> - If we don't pass filters and we don't set acceptAllDevices to true, we should get typeError
> - If we want to use some additional services beside services passed in filter, we should pass them in optionalServices


```
navigator.bluetooth.requestDevice({ filters: [{ services: ['battery_service'] }] })
```
requestDevice returns promise with device found if filter matches. 

##### BluetoothDevice
After getting device object, we have access to devices functions. From this point we can either connect to the device found, or we can just listen for advertisement of that device without connecting to it. Let's connect to the Bluetooth remote GATT Server which holds the service and characteristic definitions.

```
.then(function (device) {
	return device.gatt.connect())
```
device.gatt.connect() returns promise with server found.

We are also able to watch for advertisement from requested device. 
```
...
device.watchAdvertisements();
device.addEventListener('advertisementreceived', function (event) {
	 console.log(event);
});
```

If we want to stop listening for advertisement we can call unwatchAdvertisement() from that same device.

##### BluetoothRemoteGATTServer
As a return from connect(), we get GATTServer. From this point, we are able to check for services, and further on, for characteristics from that services.
```
.then(function(server) {
	return server.getPrimaryService('battery_service')
```

> **Note:**

> Beside getPrimaryService() we can also use getPrimaryServices(), where we pass array of services, and in return we get array of services matched

server.getPrimaryService() returns promise with found service (if it's available).


##### BluetoothRemoteGATTService
Now we have service found from server, and we are able to check for characteristic on that service. 
```
.then(function(service) {
	return service.getCharacteristic('battery_level')
```
> **Note:**

> - We can provide name of the characteristic from the list of [standardized Bluetooth GATT characteristics](https://www.bluetooth.com/specifications/gatt/characteristics). We can also provide uuid of characteristic wanted in form of 16 bit or 128 bit uuid.
> - Beside getCharacteristic() we can also use getCharacteristics(), where we pass array of characteristic, and in return we get array of characteristic matched

getCharacteristic() returns promise with found characteristic, if it's available.

##### BluetoothRemoteGATTCharacteristic
Now we are able to get some readouts from bluetooth device, via characteristics. We can use readValue() function in order to read current characteristic value, or writeValue() to write some new value to it. Note that we can also add a characteristicvaluechanged event listener on a characteristic to handle reading its value.
```
.then(function(characteristic) {
	// read current characteristic value
	return characteristic.readValue()
		.then(function(value) {
		// parsing value
		console.log('Battery percentage is ' + value.getUint8(0));
```

Listening for value change:
```
...
.then(function(characteristic) {
	 // Set up event listener for when characteristic value changes
	 characteristic.addEventListener('characteristicvaluechanged', handleBatteryLevelChanged;

function handleBatteryLevelChanged(event) {
  let batteryLevel = event.target.value.getUint8(0);
  console.log('Battery percentage is ' + batteryLevel);
}
```
Write to bluetooth characteristic:
```
...
.then(function(characteristic) {
  var value = Uint8Array.of(1);
  return characteristic.writeValue(value);
})
```
We can also get characteristic descriptor:
```
...
.then(function(characteristic) {
  return characteristic.getDescriptor(0x2902)
```

> **Note:**
>  - Beside getDescriptor() we can also use getDescriptors(), where we pass array of descriptors, and in return we get array of descriptors matched
>  - We can provide name of the descriptor from the list of [standardized Bluetooth GATT descriptors](https://www.bluetooth.com/specifications/gatt/descriptors). 


getDescriptor() returns promise with found descriptor if it is available.

##### BluetoothRemoteGATTDescriptor

We can read values from descriptor:
```
...
.then(function(characteristic) {
  return characteristic.getDescriptor(0x2902)
	  .then(function(descriptor) {
			return descriptor.readValue()
				.then(function(value) {
					console.log(value);
				})
```
and write on descriptor...
```
...
.then(function(characteristic) {
  return characteristic.getDescriptor(0x2902)
	  .then(function(descriptor) {
		  let encoder = new TextEncoder('utf-8');
		  let userDescription = encoder.encode('Defines the time between measurements.');
		  return descriptor.writeValue(userDescription)
```

##### Error handling
At the end of promise chain, as second parameter we can add error handling function, in order to catch possible errors.

```
...
     }, function (error) {
         console.warn('Error found: ' + error);
     });
```

#### Final code
```
navigator.bluetooth.requestDevice({ filters: [{ services: ['battery_service'] }] 
})
// return promise with device found
.then(function (device) {
	// trying to connect from gattServer
	return device.gatt.connect()
		// if connected, promise returns gattServer
		.then(function(server) {
			// request for gattService (matches with filter)
			return server.getPrimaryService('battery_service')
				.then(function(service) {
					// request for gattCharacteristic
					return service.getCharacteristic('battery_level')
						.then(function(characteristic) {
							// read current characteristic value
							return characteristic.readValue()
								.then(function(value) {
								  // parsing value
								  console.log('Battery percentage is ' + value.getUint8(0));
                                 })
                         })
                 })
           })
      }, function (error) {
         console.warn('Error found: ' + error);
 });
```

 
----------

#### requestLEScan()

Besides requestDevice(), with Blueapp Web Bluetooth library we can listen for advertisement of particular device without connecting to it. Just like in requestDevice(), we can pass either filter or acceptAllAdvertisement set to true in options Object inside parameter. In addition, we can add keepRepeatedDevices in same options Object in we want to get advertisement from same device.
After requesting for scan, we can attach eventListener to check for advertisement of filtered device, and parse readout from it.

> **Note:**
>  We must either pass filters, or set acceptAllAdvertisement to true. Otherwise we should get typeError.

```
navigator.bluetooth.requestLEScan({
  filters: [{manufacturerData: {0x004C: {}}}],
  options: {
    keepRepeatedDevices: true
  }
}).then(function() {
  // listening for event for new advertisement
  navigator.bluetooth.addEventListener('advertisementreceived', function(event) {
    // parsing readout data
    let data = event.manufacturerData.get(0x004C);
    let result = data.getUint16(18, false);
    console.log(result);
  });
})
``` 


----------


After we created our new application, and setup our Blueapp account, we have to post our new application on some hosting service. Note that you can use [Github Pages](https://pages.github.com/) to host your application. When we get url of that app, we can fill the form on Add Application page on Blueapp.io. Now we should have our application available in Applications.