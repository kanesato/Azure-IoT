
[Back to the demo's homepage](../../IoTDigitalTwinDemo.md#-azure-digital-twins-)
<br>

> ### Reference links
- 【Azure Digital Twins】IoTデバイスの状態を可視化する（前編）<br>
(https://blog.jbs.co.jp/entry/2023/09/26/170454)<br>

- 【Azure Digital Twins】IoTデバイスの状態を可視化する（後編）<br>
(https://blog.jbs.co.jp/entry/2023/09/27/115355)<br>


- ### Create two models on a specific Digital Twins instance 
```bash
az dt model create -n "adt-demo-dt.api.jpe.digitaltwins.azure.net" --models /Volumes/ExtraDisk/Github/Azure-IoT/articles/Resources/Models-Twins/Room.json
```

```bash
az dt model create -n "adt-demo-dt.api.jpe.digitaltwins.azure.net" --models /Volumes/ExtraDisk/Github/Azure-IoT/articles/Resources/Models-Twins/Thermostat.json
```

- ### Create two twins on a specific Digital Twins instance
```bash
az dt twin create -n "adt-demo-dt.api.jpe.digitaltwins.azure.net" --dtmi "dtmi:sample:room;2" --twin-id room
```

```bash
az dt twin create -n "adt-demo-dt.api.jpe.digitaltwins.azure.net" --dtmi "dtmi:sample:DigitalTwins:thermostat;1" --twin-id thermostat
```

- ### Update a relationship between two twins on a specific Digital Twins instance
```bash
az dt twin relationship create -n "adt-demo-dt.api.jpe.digitaltwins.azure.net" --relationship-id room --relationship contains --twin-id room --target thermostat
```

<br>
<br>
<br>

## Reference
- room.json
<br>
```bash
{
    "@id": "dtmi:sample:room;2",
    "@context": "dtmi:dtdl:context;2",
    "@type": "Interface",
    "displayName": "room",
    "contents": [
      {
        "@type": "Property",
        "name": "RoomName",
        "schema": "string"
      },
      {
        "@type": "Relationship",
        "name": "contains"
      }
    ]
  }
```

- thermostat.json
<br>
```bash
{
    "@id": "dtmi:sample:DigitalTwins:thermostat;1",
    "@context": "dtmi:dtdl:context;2",
    "@type": "Interface",
    "displayName": "thermostat",
    "contents": [
      {
        "@type": "Property",
        "name": "DisplayName",
        "schema": "string"
      },
      {
        "@type": "Property",
        "name": "Temperature",
        "schema": "double"
      }
    ]
  }
```