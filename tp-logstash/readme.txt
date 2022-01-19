=== installation de logstash sur la vm linux

wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

sudo apt-get install apt-transport-https

echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list

sudo apt-get update

sudo apt-get install logstash

sudo systemctl start logstash

sudo lsof -i -P -n | grep logstash

============= Mise en place de la config de logstash

1 copier C:\Users\FR21320\Documents\mesFormations\IPI\Lacanette\formation\ELK\tp\tp-logstash\etc 
dans /etc/logstash/conf.d sur la VM.


=== Execution de logstash
2 lancer logstash : sudo systemctl start logstash
  verifier que le port 9600 est bien disponible : sudo lsof -i -a | grep logstash

3 tail -f /var/log/logstash/logstash-plain.log 

4 tail -f /tmp/output.log

5 ajouter des lignes dans /etc/logstash/files/tgv.csv

6 voir l'ajout dans  /tmp/output.log
