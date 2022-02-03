# flow03-node-red
Monitoreo de temperaturas en broker público + panel-switch (ver. 2)

### Clases v1-26/01/2022, v2-02/02/2022. 
 
- Se recomienda en vez de usar `broker.hivemq.com`, en una terminal: `nslookup broker.hivemq.com`
   IP: `35.157.158.119`
 - Recuerda que todos los IDs (-i) deben ser diferentes.

### Consola: 
- Terminal-1: `node-red`
 - Terminal-2: `mosquitto_pub -h broker.hivemq.com -t sic/flow3/temp -i alberto_chih -q 2 -m "{\"id\": \"Alberto Pacheco\", \"temp\": 5, \"humedad\": 80, \"place\" : \"Chihuahua\"}"`
 - Terminal-3: `mosquitto_sub -h 35.157.158.119 -p 1883 -i alberto_chih_21 -q 2 -t sic/flow3/temp`
 - Terminal-4: `mosquitto_sub -h 35.157.158.119 -p 1883 -i alberto_chih_22 -q 2 -t sic/flow3/switch/hugovargas`

## Dashboard:
![flow3 screen v2](https://user-images.githubusercontent.com/95945745/152283343-a8f20a23-4540-4512-a688-4ddb3b38708c.jpg)

## Flow:
![flow3 nodes v2](https://user-images.githubusercontent.com/95945745/152283800-bec012e8-c89d-4bdc-9dd3-274c0a018875.jpg)

## Function: f1
```javascript
  msg.payload = msg.payload.id
  return msg;
```

## Function: f2
```javascript
  msg.payload = msg.payload.temp
  return msg;
```

## Function: f3
```javascript
  msg.topic = msg.payload.id;
  msg.payload = msg.payload.temp;
  return msg;
```


## Function: send text
```javascript
  msg.payload = msg.payload? "Alberto encendió switch" : "Alberto apagó el switch";
  return msg;
```

## Function: send temp
```javascript
 msg.payload = { 
   "id": "Alberto Pacheco", 
   "temp": (msg.payload? "10" : "20") 
 };
 return msg;
```
 
