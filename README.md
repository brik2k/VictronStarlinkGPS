This project includes a Node-Red flow that runs on a Victron Cerbo GX to pull gps data from a local Starlink dish and publish it to the VRM portal for logging and display. This is far from polished so any recommendations are welcome, though they might be ignored. ;-)

<img width="403" alt="image" src="https://github.com/brik2k/VictronStarlinkGPS/assets/19332985/9af460fb-8e8b-4bc8-aec3-090dc9436a29">

This flow does the following:
 1. Uses freakent's dbus-mqtt-devices driver (https://github.com/freakent/dbus-mqtt-devices) to register a 'starlink01' device with a gps service on the Victron dbus. 
 2. Uses node-red-contrib-grpc to send a grpc call to a local Starlink dish to retrieve gps data. See https://github.com/sparky8512/starlink-grpc-tools for how to enable pulling location data from Dishy.
 3. Publishes the gps lat, long, and altitude to the Victron MQTT so it's logged and displayed on the Victron VRM Portal. 
 
Things to tweak:
 1. The grpc .proto file configuration is probably a mess and should be cleaned up by someone who knows what they're doing.
 2. Probably need to add some error handling to the grpc call process.
 3. There the likely many ways to optimize the code for parsing and publishing the gps data to MQTT. 

<img width="660" alt="image" src="https://github.com/brik2k/VictronStarlinkGPS/assets/19332985/53419eb2-8118-4eda-bab7-7866e49ef594">
