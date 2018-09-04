# Elastic Stack - Using Docker


All the imaages used are based on the official Docker images:

* [elasticsearch](https://github.com/elastic/elasticsearch-docker)
* [logstash](https://github.com/elastic/logstash-docker)
* [kibana](https://github.com/elastic/kibana-docker)

We mount the config files using docker volumes. This makes them persistent and allows us to make changes without doing a docker exec

For spining up the stack we will use the `docker-compose` command

```console
$ docker-compose up -d
```





