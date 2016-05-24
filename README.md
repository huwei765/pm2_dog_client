# pm2_dog_client
the monitor tool of node.js project

Node.js项目的监控平台（运维人员使用）

部署方案
1. pm2_dog_server部署在APP Project服务器上，这台服务器的node.js项目必须是由pm2 启动并进行监控的（比如：pms start app.js） 
2. pm2_dog_client部署在监控运维服务器上，它的重要性是：配置config.json,里面指定了它所监控的服务器列表

原理：
1. pm2 启动的node.js项目，pm2会做监控
2. pm2_dog_server在底层就是通过pm2的命令来采集数据或驱动数据，比如底层封装了pm2 list命令
3. pm2_dog_client 与pm2_dog_server通过socket通信（C/S结构）获取server端的数据
