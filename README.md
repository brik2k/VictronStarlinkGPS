This project includes a Node-Red flow that runs on a Victron Cerbo GX to pull gps data from a local Starlink dish and publish it to the VRM portal for logging and display. 

This flow does the following:
 1. Uses freakent's dbus-mqtt-devices driver (https://github.com/freakent/dbus-mqtt-devices) to register a 'starlink01' device with a gps service on the Victron dbus. 
 2. Uses node-red-contrib-grpc to send a grpc call to a local Starlink dish to retrieve gps data. See https://github.com/sparky8512/starlink-grpc-tools for how to enable pulling location data from Dishy.
 3. Publishes the gps lat, long, and altitude to the Victron MQTT so it's logged and displayed on the Victron VRM Portal. 
 
Things to tweak:
 1. The grpc .proto file configuration is probably a mess and should be cleaned up by someone who knows what they're doing.
 2. Probably need to add some error handling to the grpc call process.
