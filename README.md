# Elasticsearch Docker Setup

Steps to setup elastic search and kibana using docker

## Install Docker

> Follow platform specific instructions

## Install and Run Elasticsearch

```bash
docker network create elastic
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.12.1
docker run --name es01-test --net elastic -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.12.1
```

## Install and Run Kibana

```bash
docker pull docker.elastic.co/kibana/kibana:7.12.1
docker run --name kib01-test --net elastic -p 5601:5601 -e "ELASTICSEARCH_HOSTS=http://es01-test:9200" docker.elastic.co/kibana/kibana:7.12.1
```

Visit [http://localhost:5601](http://localhost:5601) to access the kibana dashboard