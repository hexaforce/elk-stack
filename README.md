# elk-stack

# GET elk
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.2.4.tar.gz  
wget https://artifacts.elastic.co/downloads/logstash/logstash-6.2.4.tar.gz  
wget https://artifacts.elastic.co/downloads/kibana/kibana-6.2.4-linux-x86_64.tar.gz  

tar -zxvf elasticsearch-6.2.4.tar.gz  
tar -zxvf logstash-6.2.4.tar.gz  
tar -zxvf kibana-6.2.4-linux-x86_64.tar.gz  


# Elasticsearch  
vi elasticsearch-6.2.4/config/elasticsearch.yml  
export ES_TMPDIR=/var/tmp/elasticsearch  

bash -ex elasticsearch-6.2.4/bin/elasticsearch  


# Logstash  
sudo mkdir /etc/conf.d/logstash  
sudo vi /etc/conf.d/logstash/logstash-filter.conf  

bash -ex logstash-6.2.4/bin/logstash  -f /etc/conf.d/logstash  


# Kibana  
rm -rf kibana-6.2.4-linux-x86_64/node  
vi kibana-6.2.4-linux-x86_64/config/kibana.yml  
> server.host: 0.0.0.0  
> elasticsearch.url: "http://127.0.0.1:9200"  

bash -ex kibana-6.2.4-linux-x86_64/bin/kibana  
