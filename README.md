emqx_bridge_nsq
====================

EMQX的NSQ桥接插件  
基于4.2.14版本的[EMQX][emqx]和[ENSQ][ensq]进行开发  

This is a  plugin for the EMQ X broker and nsq.  
Develop based on [EMQX][emqx](version 4.2.14) and [ENSQ][ensq]

[emqx]:https://github.com/emqx/emqx-rel/tree/v4.2.14
[ensq]:https://github.com/project-fifo/ensq

Plugin Config
-------------
Config Path:
```
etc/plugins/emqx_bridge_nsq.config
```
```
[
  {emqx_bridge_nsq, 
    [{values, [
      {bootstrap_broker, "localhost"},
      {nsq_producer_topic, data_topic},
      {nsq_producer_topic2, device_status}
    ]}
  ]}
].
```

Configuration item description
-----------------
bootstrap_broker : `host of nsqlookupd`  
nsq_producer_topic : `topic name(for data)`  
nsq_producer_topic2 : `topic name(for device_status)`

Start the topic name with lowercase like `tOPIC`

Example
-----------------
When MQTT publish a message
```
"type":"published",
"topic":"06cf442d-2f6b-72a7-85f7-2fc8423abba6/Pub",
"from":"06cf442d-2f6b-72a7-85f7-2fc8423abba6",
"payload":"{\"temp\": 27578,\"humi\": 56759,\"tvoc\": 7,\"co2\": 459,\"voci\": 101,\"pm1\": 20,\"pm2dot5\": 30,\"pm10\": 33,\"co\": 625,\"ch2o\": 12060}"
```
When MQTT disconnect
```
"type":"disconnected",
"device_id":"06cf442d-2f6b-72a7-85f7-2fc8423abba6",
"username":"emqx",
"reason":"normal"
```
For more information on `disconnect reason`, see [EMQX documentation][1]

[1]: https://www.emqx.io/docs/zh/v4.4/faq/use-guide.html#mqtt-%E5%AE%A2%E6%88%B7%E7%AB%AF%E6%96%AD%E5%BC%80%E8%BF%9E%E6%8E%A5%E7%BB%9F%E8%AE%A1

License
-------

Apache License Version 2.0

Author
------

izum1
