# particle-ymodem
Basic implementation of the Ymodem-protocol as implemented in Particle devices. Currently created and tested only to send firmware files to a Particle Photon.

##### Install using NPM
```
npm install particle-ymodem
npm install serialport
```

##### Use in application

```js
var lightYModem = require('particle-ymodem');
var serialPort = require("serialport");
var fs = require('fs');

var file = fs.readFileSync('./firmware.bin');
var serialPort = new serialPort.SerialPort('/dev/cu.usbmodemfd131', {baudrate: 28800}, false);
var progressCallback = function(val){  console.log( Math.round(val.current/val.total) + '%' );}
var logCallback = console.log;

var modem = new lightYModem();
modem.transfer(file, serialPort, progressCallback, logCallback);
```

