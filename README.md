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

<a name="Rega"></a>

## Rega
**Kind**: global class  

* [Rega](#Rega)
    * [new Rega(options)](#new_Rega_new)
    * _instance_
        * [.exec(script, [callback])](#Rega+exec) ⇒ <code>void</code>
        * [.script(file, [callback])](#Rega+script) ⇒ <code>void</code>
        * [.getChannels(callback)](#Rega+getChannels) ⇒ <code>void</code>
        * [.getValues(callback)](#Rega+getValues) ⇒ <code>void</code>
        * [.getPrograms(callback)](#Rega+getPrograms) ⇒ <code>void</code>
        * [.getVariables(callback)](#Rega+getVariables) ⇒ <code>void</code>
        * [.getRooms(callback)](#Rega+getRooms) ⇒ <code>void</code>
        * [.getFunctions(callback)](#Rega+getFunctions) ⇒ <code>void</code>
        * [.setVariable(id, value, [callback])](#Rega+setVariable) ⇒ <code>void</code>
        * [.startProgram(id, [callback])](#Rega+startProgram) ⇒ <code>void</code>
        * [.setProgram(id, active, [callback])](#Rega+setProgram) ⇒ <code>void</code>
        * [.setName(id, name, [callback])](#Rega+setName) ⇒ <code>void</code>
    * _inner_
        * [~scriptCallback](#Rega..scriptCallback) : <code>function</code>

<a name="new_Rega_new"></a>

### new Rega(options)

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| options | <code>object</code> |  | object |
| options.host | <code>string</code> |  | hostname or IP address of the Homematic CCU |
| [options.language] | <code>string</code> | <code>&quot;de&quot;</code> | language used for translation of placeholders in variables/rooms/functions |
| [options.disableTranslation] | <code>boolean</code> | <code>false</code> | disable translation of placeholders |
| [options.tls] | <code>boolean</code> | <code>false</code> | Connect using TLS |
| [options.inSecure] | <code>boolean</code> | <code>false</code> | Ignore invalid TLS Certificates |
| [options.auth] | <code>boolean</code> | <code>false</code> | Use Basic Authentication |
| [options.user] | <code>string</code> |  | Auth Username |
| [options.pass] | <code>string</code> |  | Auth Password |
| [options.port] | <code>number</code> | <code>8181</code> | rega remote script port. Defaults to 48181 if options.tls is true |

<a name="Rega+exec"></a>

### rega.exec(script, [callback]) ⇒ <code>void</code>
Execute a rega script

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| script | <code>string</code> | string containing a rega script |
| [callback] | [<code>scriptCallback</code>](#Rega..scriptCallback) | callback |

<a name="Rega+script"></a>

### rega.script(file, [callback]) ⇒ <code>void</code>
Execute a rega script from a file

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| file | <code>string</code> | path to script file |
| [callback] | [<code>scriptCallback</code>](#Rega..scriptCallback) | callback |

<a name="Rega+getChannels"></a>

### rega.getChannels(callback) ⇒ <code>void</code>
Get all devices and channels

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>Rega~channelCallback</code> | callback |

<a name="Rega+getValues"></a>

### rega.getValues(callback) ⇒ <code>void</code>
Get all devices and channels values

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>Rega~valuesCallback</code> | callback |

<a name="Rega+getPrograms"></a>

### rega.getPrograms(callback) ⇒ <code>void</code>
Get all programs

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>Rega~programsCallback</code> | callback |

<a name="Rega+getVariables"></a>

### rega.getVariables(callback) ⇒ <code>void</code>
Get all variables

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>Rega~variablesCallback</code> | callback |

<a name="Rega+getRooms"></a>

### rega.getRooms(callback) ⇒ <code>void</code>
Get all rooms

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>Rega~roomsCallback</code> | callback |

<a name="Rega+getFunctions"></a>

### rega.getFunctions(callback) ⇒ <code>void</code>
Get all functions

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>Rega~functionsCallback</code> | callback |

<a name="Rega+setVariable"></a>

### rega.setVariable(id, value, [callback]) ⇒ <code>void</code>
Set a variables value

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | - |
| value | <code>number</code> \| <code>boolean</code> \| <code>string</code> | - |
| [callback] | <code>function</code> | callback |

<a name="Rega+startProgram"></a>

### rega.startProgram(id, [callback]) ⇒ <code>void</code>
Execute a program

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | - |
| [callback] | <code>function</code> | callback |

<a name="Rega+setProgram"></a>

### rega.setProgram(id, active, [callback]) ⇒ <code>void</code>
Activate/Deactivate a program

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | - |
| active | <code>boolean</code> | - |
| [callback] | <code>function</code> | callback |

<a name="Rega+setName"></a>

### rega.setName(id, name, [callback]) ⇒ <code>void</code>
Rename an object

**Kind**: instance method of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | - |
| name | <code>string</code> | - |
| [callback] | <code>function</code> | callback |

<a name="Rega..scriptCallback"></a>

### Rega~scriptCallback : <code>function</code>
**Kind**: inner typedef of [<code>Rega</code>](#Rega)  

| Param | Type | Description |
| --- | --- | --- |
| error | <code>Error</code> |  |
| output | <code>string</code> | the scripts output |
| variables | <code>Object.&lt;string, string&gt;</code> | contains all variables that are set in the script (as strings) |


## Related projects

* [node-red-contrib-ccu](https://github.com/ptweety/node-red-contrib-ccu) - Node-RED nodes for the Homematic CCU.
* [hm-binrpc](https://github.com/ptweety/hm-binrpc) - Node.js client/server for the Homematic BINRPC protocol.
* [hm-xmlrpc](https://github.com/ptweety/hm-xmlrpc) - Node.js client/server for the Homematic XMLRPC protocol.


## License

MIT (c) Sebastian Raff

[mit-badge]: https://img.shields.io/badge/License-MIT-blue.svg?style=flat
[mit-url]: LICENSE
