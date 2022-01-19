# Demarrage de tous les services : beat, kafka, zookeeper, apache, logstash, kibana, elastic ...
docker-compose up -d

# si pb de memoire windows
wsl -d docker-desktop
sysctl -w vm.max_map_count=262144


# kibana
http://localhost:5601

# Verifier les noeuds ELK :
curl -X GET "localhost:9200/_cat/nodes?v&pretty"
http://localhost:9200/_cluster/health?pretty=true

# arret
docker-compose down -v

