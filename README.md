# ELK-FILEBEAT

## Description
Docker compose to start a elk suite with filebeat log integrated (not finished yet)

## Start project

1. open a terminal at project root
2. run theses commands

```shell
docker compose -f create-certs.yml run --rm create_certs

docker compose -f elastic-docker-tls.yml up -d 
```
3. once done run this one 
```shell
docker exec es01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url https://es01:9200"
```
4. note the radomly generated passwords
5. change the kibana environnement variable in elastic-docker-tls.yml (ELASTICSEARCH_PASSWORD) file by the kibana_system generated value
6. in the filebeat.yml file use the user elastic password in 'output.elasticsearch' field
7. run commands 
```shell
docker compose stop

docker compose -f elastic-docker-tls.yml up -d
```

TODO Start Elastic search module in filebeat

## Links
- Elastic documentation for elk stack with tls enabled

https://www.elastic.co/guide/en/elastic-stack-get-started/7.15/get-started-docker.html#get-started-docker-tls

- Docker doc 

https://docs.docker.com/

- Filebeat configuration

https://www.elastic.co/guide/en/beats/filebeat/7.15/filebeat-installation-configuration.html