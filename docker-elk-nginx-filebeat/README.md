# Elastic stack (ELK) + Filebeat : monitorer Nginx

[ELK on Docker](https://github.com/deviantony/docker-elk) with Filebeat plugin. Filebeat takes in charge of streaming log file from nginx to Logstash then processing it and visualize to Kibana.

# Repertoires
├── app
│   ├── package.json
│   ├── package-lock.json
│   ├── src
│   │   └── index.js
│   └── yarn.lock
├── elasticsearch
│   ├── config
│   │   └── elasticsearch.yml
│   └── Dockerfile
├── filebeat
│   ├── config
│   │   └── filebeat.yml
│   └── Dockerfile
├── kibana
│   ├── config
│   │   └── kibana.yml
│   └── Dockerfile
├── logstash
│   ├── config
│   │   └── logstash.yml
│   ├── Dockerfile
│   └── pipeline
│       └── nginx.conf
├── nginx
│   ├── config
│   │   └── site.conf
│   ├── Dockerfile
│   └── log
│       ├── access.log
│       └── error.log
├── docker-compose.yml
├── LICENSE
└── README.md
```

- App: minimal simple Express app
- Nginx: web server for app.
- Elasticsearch: containing build image and configure for Elasticsearch
- Filebeat: containing build image and configure for Filebeat to streaming log of Nginx to Logstash
- Logstash: containing build image and configure pipeline for Logstash to process sent log file from Filebeat
- Kibana: containing build image and configure for Kibana to visualize data

# Lancer le cluster complet
```bash
docker-compose up -d
```

# Ouvrer votre navigateur pour acceder a kibana :
Then go to `http://localhost:5601` to see your data in Kibana

Default Kibana user information
- Username: elastic
- Password: changeme

# Lancement ELK : 
# voir https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html

# Verifier les noeuds ELK :
curl -X GET "localhost:9200/_cat/nodes?v&pretty"
ou
curl http://localhost:9200 -u elastic:changeme

# Ouvrer dans votre navigateur nginx pour generer un log nginx:
localhost:80

# Rappel :
5044: Logstash Beats input
5000: Logstash TCP input
9600: Logstash monitoring API
9200: Elasticsearch HTTP
9300: Elasticsearch TCP transport
5601: Kibana

# arret
docker-compose down -v


# ===========================

# si pb de memoire windows
wsl -d docker-desktop
sysctl -w vm.max_map_count=262144

# si pb de memoire ubuntu
sudo sysctl -w vm.max_map_count=262144


# si pb d'espace disque VM
# Aller dans vbx : https://www.malekal.com/virtualbox-reduire-augmenter-la-taille-du-disque-virtuel/
ouvrir le media avec control d
puis dans proprietes, augmenter la taille du disque de la VM
Lancer la VM et installer gparted : : https://lecrabeinfo.net/redimensionner-agrandir-reduire-une-partition-sur-linux.html
sudo apt install gparted
gparted

# Install docker-compose : voir https://phoenixnap.com/kb/install-docker-compose-ubuntu
sudo apt-get update
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose -version

