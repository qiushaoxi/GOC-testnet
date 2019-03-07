# docker 方式启动测试网节点

## 修改配置
修改docker-compose.yaml文件
```
version: "2"

services:
  goc:
    image: qiushaoxi/goc:10230fe
    command: nodeos --data-dir /goc/data --config-dir /goc/config  --delete-all-blocks --genesis-json=/goc/config/genesis.json
    hostname: enunoded
    ports:
      - 8888:8888
      - 9876:9876
    volumes:
      - /Users/qiushaoxi/dev/goc/testnet/config:/goc/config
      - /Users/qiushaoxi/dev/goc/testnet/data:/goc/data
```
- command 启动参数根据需求修改，该参数为初次启动参数
- /Users/qiushaoxi/dev/goc/testnet/config 修改为自己的配置目录，必须包含config.ini 和 genesis.json
- /Users/qiushaoxi/dev/goc/testnet/data 修改为自己的数据目录

## 启动容器

在该目录执行 docker-compose up -d 
