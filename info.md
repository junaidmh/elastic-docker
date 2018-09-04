# ELK - Log Solution


Based on the official Docker images:

* [elasticsearch](https://github.com/elastic/elasticsearch-docker)
* [logstash](https://github.com/elastic/logstash-docker)
* [kibana](https://github.com/elastic/kibana-docker)


Start the ELK stack using `docker-compose`:

```console
$ docker-compose up
$ docker-compose up -d
```


Kibana UI

[http://localhost:5601](http://localhost:5601.

Ports:

* 5000: Logstash TCP input
* 5601: Kibana
* 9200: Elasticsearch HTTP
* 9300: Elasticsearch TCP transport

while :; do cat access_log_2018*.log | nc localhost 5000; sleep 5; done

