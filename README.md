# Elastic Stack - Using Docker

Aim:-

A templatized ELK setup for centralized logging across Application, Load Balancer, Webserver & Infra. Using pre-defined Logstash patterns for log parsing and actionable analysis.  1 Click docker container based, customizable ELK setup for POC’s. 

Uses:-
 
* Reduces the learning curve for ELK.
* Ready to use dashboards with all standard metrics.
* Brings transparency across App, webserver & infra logs & events 
 


All the imaages used are based on the official Docker images:

* [elasticsearch](https://github.com/elastic/elasticsearch-docker)
* [logstash](https://github.com/elastic/logstash-docker)
* [kibana](https://github.com/elastic/kibana-docker)

We mount the config files using docker volumes. This makes them persistent and allows us to make changes without doing a docker exec

For spining up the stack we will use the `docker-compose` command

```console
$ docker-compose up -d
```





