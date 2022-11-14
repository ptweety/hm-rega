# hm-rega

This is a fork of [homematic-rega](https://github.com/hobbyquaker/homematic-rega) by Sebastian Raff.

[![License][mit-badge]][mit-url]

> Node.js Homematic CCU ReGaHSS Remote Script Interface

This module encapsulates the communication with the "ReGaHSS" - the logic layer of the Homematic CCU. 

* execute arbitrary scripts
* get names and ids of devices and channels
* get variables including their value und meta data
* set variable values
* get programs
* execute programs
* activate/deactivate programs
* get rooms and functions including assigned channels
* rename objects

i18n placeholders (e.g. `${roomKitchen}`) are translated by default.

You can find offical and inoffical documentation of the homematic scripting language at 
[wikimatic.de](http://www.wikimatic.de/wiki/Script_Dokumentation).

Pull Requests welcome! :)


## Install

`$ npm install homematic-rega`


## Usage Example

```javascript
const Rega = require('homematic-rega');

const rega = new Rega({host: '192.168.2.105'});

rega.exec('string x = "Hello";\nWriteLine(x # " World!");', (err, output, objects) => {
    if (err) {
        throw err;
    } 
    console.log('Output:', output);
    console.log('Objects:', objects);
});

rega.getVariables((err, res) => {
    console.log(res);
});
```


## API

