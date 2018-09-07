## Quickstart using Docker Compose

Create the following docker-compose.yml file.

	elkx:
	  image: sebp/elkx
	  ports:
	    - "5601:5601"
	    - "9200:9200"
	    - "5044:5044"
	  environment:
	    - ELASTIC_BOOTSTRAP_PASSWORD="changeme"

Start a container using docker-compose.

	$ docker-compose up
	Creating elkxdocker_elkx_1
	Attaching to elkxdocker_elkx_1
	elkx_1  | ERROR: Setting [bootstrap.pass] does not exist in the keystore.
	elkx_1  |  * Starting periodic command scheduler cron
	elkx_1  |    ...done.
	elkx_1  |  * Starting Elasticsearch Server
	elkx_1  |    ...done.
	elkx_1  | waiting for Elasticsearch to be up (1/30)
	...

In another shell, open a bash session in the running container (replacing `<name of the running container>` with the right value), and use X-Pack's `setup-passwords` tool (located in `$ES_HOME/bin/x-pack`) to set the passwords for the built-in users.

	$ docker exec -it <name of the running container> bash
	# $ES_HOME/bin/x-pack/setup-passwords interactive
	Initiating the setup of reserved user elastic,kibana,logstash_system passwords.
	You will be prompted to enter passwords as the process progresses.
	Please confirm that you would like to continue [y/N]y


	Enter password for [elastic]: changeme
	Reenter password for [elastic]: changeme
	Enter password for [kibana]: changeme
	Reenter password for [kibana]: changeme
	Enter password for [logstash_system]: changeme
	Reenter password for [logstash_system]: changeme
	Changed password for user [kibana]
	Changed password for user [logstash_system]
	Changed password for user [elastic]

Stop the container, then edit the docker-compose.yml as follows:

	elkx:
	  image: sebp/elkx
	  ports:
	    - "5601:5601"
	    - "9200:9200"
	    - "5044:5044"
	  environment:
	    - ELASTICSEARCH_USER=elastic
	    - ELASTICSEARCH_PASSWORD=changeme
	    - LOGSTASH_USER=elastic
	    - LOGSTASH_PASSWORD=changeme
	    - KIBANA_USER=kibana
	    - KIBANA_PASSWORD=changeme

Then start the container again using docker-compose up.