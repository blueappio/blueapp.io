# BlueApp.io

Coming from the platform that helps you manage and track dvices, this library enables developers to creat apps for web and mobile using web bluetooth api. You can use this library to create apps for the Blueapp platform or for your personal bluetooth needs.

### Installation

There are two ways to integrate the library into your application,

add the following line to your index.thml

```
<script src="https://blueappio.github.io/blueapp.io/blueapp.io.min.js"></script>
```

or, install via bower

```
bower install blueapp.io --save
```

### Web Bluetooth API Supported:
<table>
  <tbody>
    <tr>
      <th>Functions</th>
    </tr>
    <tr>
      <td><b>Device Discovery</b></td>
    </tr>
    <tr>
      <td>
        <dl>
          <dt>navigator.bluetooth.requestDevice()</dt> 
          <dd>If using on Blueapp platform, filters are ignored.</dd>
          <dd> If using library outside of blueapp, use the following supported filters:
            <br>
            <ul>
              <li>'name': which will look for a device(s) that matches the name given.
              <li>'service': which can be an array of 16 bit or 128 bit uuids. These uuids represent services uuids that are advertised by the bluetooth device.
              <li>'namePrefix': which will look for a device(s) who's name matches the prefix given.
            </ul>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td><b>Bluetooth Device</b></td>
    </tr>
    <tr>
      <td>
        <dl>
          <dt>connect()</dt>
          <dd>Attempts to connect internally up to three times</dd>
        </dl>
      </td>
    </tr>
    <tr><td><b>Services</b></td></tr>
    <tr><td><dl><dt>getPrimaryService()</dt></dl></td></tr>
    <tr><td><dl><dt>getCharacteristic()</dt></dl></td></tr>
    <tr><td><b>Characteritics</b></td></tr>
    <tr><td><dl><dt>getDescriptor()</dt></dl></td></tr>
    <tr><td><dl><dt>readValue()</dt></dl></td></tr>
    <tr><td><dl><dt>writeValue()</dt></dl></td></tr>
    <tr><td><b>Descriptors</b></td></tr>
    <tr><td><dl><dt>readValue()</dt></dl></td></tr>
    <tr><td><dl><dt>writeValue()</dt></dl></td></tr>
    <tr><th>Properties</th></tr>
    <tr><td><b>Services</b></td></tr>
    <tr><td><dl><dt>uuid</dt></dl></td></tr>
    <tr><td><b>Characteritics</b></td></tr>
    <tr>
      <td>
      <dl><dt>
        properties
       </dt>
        <dd>Supported: broadcast, read,  writeWithoutResponse, write, notify and indicate
        <dd>
        </dl>
      </td>
    </tr>
    <tr><td><dl><dt>uuid</dt></dl></td></tr>
    <tr><td><dl><dt>service</dt></dl></td></tr>
    <tr><td><b>Descriptors**</b></td></tr>
    <tr><td><dl><dt>uuid</dt></dl></td></tr>
    <tr><td><dl><dt>characteristic</dt></dl></td></tr>
    <tr><th>Events</th><tr>
    <tr><td><b>Characteritics</b></td><tr>
    <tr><td><dl><dt>oncharacteristicvaluechanged</dt></dl></td><tr>
  </tbody>
</table>

### Extra Material

Follow Web Bluetooth Specification to build your Bluetooth App. [Click here for more info on Web Bluetooth](https://www.w3.org/community/web-bluetooth/)

Go to [BlueApp.io](https://www.blueapp.io) create an account, add the link to your application. 
Go to Organization->(Click your organization name)->My Applications

Note: You can use [Github Pages](https://pages.github.com/) to host your application.

[Check the other repos for more examples.](https://github.com/blueappio)
