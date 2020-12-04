###how to install elasticsearch with kibana

#if you use the "docker WSL 2 enngine" then run the 3 command bellow, 1 at the time:

```
sysctl -w vm.max_map_count=262144
wsl -d docker-desktop
exit
```
#create a network for es-stack

```docker network create es-stack-network```

#download and install elastic search

```docker run -d --name elasticsearchdb --net es-stack-network -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:6.8.13```

#download and install kibana

```docker run -d --name kibana-es-ui --net es-stack-network -e "ELASTICSEARCH_URL=http://elasticsearchdb:9200"  -p 5601:5601 kibana:6.8.13```



