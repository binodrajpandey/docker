## File structure
```
.
├── README.md
├── data
│   ├── elasticsearch
│   ├── filebeat
│   │   ├── filebeat.yml
│   │   └── logs
│   │       └── test.log
│   ├── kibana
│   └── logstash
│       └── pipeline
│           └── logstash.conf
└── docker-compose.yml
```

go to kibana UI console- localhost and create an index pattern `logstash-*` to see the indexed data
[References](https://www.javainuse.com/spring/springboot-microservice-elk)
