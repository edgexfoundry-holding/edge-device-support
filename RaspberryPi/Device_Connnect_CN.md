#链接设备

[![README](https://img.shields.io/badge/English-brightgreen)](./Device_Connect.md)

EdgeX Foundry 提供[随机数设备服务](https://github.com/edgexfoundry/device-random)，可用于测试，它返回可配置范围内的随机数。运行此服务的配置在本指南开头下载的 docker-compose.yml 文件中，但默认情况下会禁用。要启用它，请在 docker-compose.yml 中解开以下行：
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
然后，您可以通过以下方式启动随机设备服务：
```
docker-compose up -d device-random
```
设备服务将注册名为 Random-Integer-Generator01 的设备，该设备将开始将其随机数字读数发送到 EdgeX 中。<br>
您可以通过查询为 Random-Integer-Generator01 发送的最后 10 个事件记录的 EdgeX 核心数据服务来验证这些读数是否正在发送：
```
curl http://localhost:48080/api/v1/event/device/Random-Integer-Generator01/10
```

