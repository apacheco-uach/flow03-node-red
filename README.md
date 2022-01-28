# flow03-node-red
Monitoreo de temperaturas en broker público

### Creado en clase con Hugo Vargas el 26/01/2022. 
 
- Se recomienda en vez de usar `broker.hivemq.com`, en una terminal: `nslookup broker.hivemq.com`
   IP: `35.157.158.119`
 - Recuerda que todos los IDs (-i) deben ser diferentes.

### Instrucciones: 
- Terminal-1: `node-red`
 - Terminal-2: `mosquitto_pub -h broker.hivemq.com -t sic/flow3/temp -i alberto_chih -q 2 -m "{\"id\": \"Alberto Pacheco\", \"temp\": 5, \"humedad\": 80, \"place\" : \"Chihuahua\"}"`

![flow3](https://user-images.githubusercontent.com/95945745/151636816-0d155e56-4dc4-4ba6-a706-4ad2a49bbeec.jpg)
