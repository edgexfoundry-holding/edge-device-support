## Connecting a Device

[![README_CN](https://img.shields.io/badge/%E4%B8%AD%E6%96%87-brightgreen)](./Device_Connnect_CN.md)

EdgeX Foundry provides a [Random Number Device Service]((https://github.com/edgexfoundry/device-random) which is useful for testing, it returns a random number within a configurable range. Configuration for running this service is in the docker-compose.yml file, but it is disabled by default. To enable it, uncomment the following lines in your docker-compose.yml:
```
device-random:
image: edgexfoundry/docker-device-random-go:1.2.1
ports:
- "127.0.0.1:49988:49988"
container_name: edgex-device-random
hostname: edgex-device-random
networks:
- edgex-network
environment:
<<: *common-variables
Service_Host: edgex-device-random
depends_on:
- data
- command
```

Then you can start the Random device service with:<br>
```
docker-compose up -d device-random
```

The device service will register a device named Random-Integer-Generator01, which will send its random number into EdgeX..<br>
You can verify those numbers are being sent by querying the EdgeX core data service for the last 10 event records sent for Random-Integer-Generator01: <br>
```
curl http://localhost:48080/api/v1/event/device/Random-Integer-Generator01/10
```
