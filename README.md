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
    <tr><td>
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
    </td></tr>
    <tr><td><b>Bluetooth Device</b></td></tr>
    <tr><td>
        <dl>
          <dt>connect()</dt>
          <dd>Attempts to connect internally up to three times</dd>
          <dd>Returns: the connected device on success</dd>
        </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>getPrimaryService()</dt>
        <dd>
          Parameters:
          <ul>
            <li>Service UUID we are searching for. Can be 16 bit or 128 bit
            <dd> ex: "180a"</dd>
          </ul>
        </dd>
        <dd>Returns: Reference to service.</dd>
      </dl>
    </td></tr>
    <tr><td><b>Service</b></td></tr>
    <tr><td>
      <dl>
        <dt>getCharacteristic()</dt>
        <dd>
          Parameters:
          <ul>
            <li>Characteristic UUID we are searching for. Can be 16 bit or 128 bit
            <dd> ex: "220a"</dd>
          </ul>
        </dd>
        <dd>Returns: Reference to characteristic.</dd>
      </dl>
    </td></tr>
    <tr><td><b>Characteritic</b></td></tr>
    <tr><td>
      <dl>
        <dt>getDescriptor()</dt>
        <dd>
          Parameters:
          <ul>
            <li>Descriptor UUID we are searching for. Can be 16 bit or 128 bit
            <dd> ex: "180a"</dd>
          </ul>
        </dd>
        <dd>Returns: Reference to service.</dd>
      </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>readValue()</dt>
        <dd>Returns: Data buffer contain bytes from device.</dd>
      </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>writeValue()</dt>
        <dd>
          Parameters:
          <ul>
            <li>Bytes to be written.
          </ul>
        </dd>
      </dl>
    </td></tr>
    <tr><td><b>Descriptor</b></td></tr>
        <tr><td>
      <dl>
        <dt>readValue()</dt>
        <dd>Returns: Data buffer contain bytes from device.</dd>
      </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>writeValue()</dt>
        <dd>
          Parameters:
          <ul>
            <li>Bytes to be written.
          </ul>
        </dd>
      </dl>
    </td></tr>
    <tr><th>Properties</th></tr>
    <tr><td><b>Service</b></td></tr>
    <tr><td>
      <dl>
        <dt>uuid</dt>
        <dd>Identifier of the service.</dd>
      </dl>
    </td></tr>
    <tr><td><b>Characteritic</b></td></tr>
    <tr><td>
        <dl>
          <dt>properties</dt>
          <dd>Permissions of the characteristic.</dd>
          <dd>
            Supported:
            <ul>
              <li> broadcast
              <li> read
              <li> writeWithoutResponse
              <li> write
              <li> notify
              <li> indicate
            </ul>
          </dd>
        </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>uuid</dt>
        <dd>Identifier of the characteristic.</dd>
      </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>service</dt>
        <dd>Parent service reference.</dd>
      </dl>
    </td></tr>
    <tr><td><b>Descriptor</b></td></tr>
    <tr><td>
      <dl>
        <dt>uuid</dt>
        <dd>Identifier of the descriptor.</dd>
      </dl>
    </td></tr>
    <tr><td>
      <dl>
        <dt>characteristic</dt>
        <dd>Parent characteristic reference</dd>
      </dl>
    </td></tr>
    <tr><th>Events</th></tr>
    <tr><td><b>Characteritics</b></td></tr>
    <tr><td>
      <dl>
        <dt>oncharacteristicvaluechanged</dt>
        <dd>Add listener for event when trying to get notifications or indications of a characteristic</dd>
      </dl>
    </td></tr>
  </tbody>
</table>

### Extra Material

Follow Web Bluetooth Specification to build your Bluetooth App. [Click here for more info on Web Bluetooth](https://www.w3.org/community/web-bluetooth/)

Go to [BlueApp.io](https://www.blueapp.io) create an account, add the link to your application. 
Go to Organization->(Click your organization name)->My Applications

Note: You can use [Github Pages](https://pages.github.com/) to host your application.

[Check the other repos for more examples.](https://github.com/blueappio)
