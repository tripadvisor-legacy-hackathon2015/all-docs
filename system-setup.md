## ES development servers for deCODE 2015

```
es-hack-1 159.203.8.69

```


## Base server setup

Setup an Ubuntu 14.04 LTS server real quick. Now let's add java 8.

```
add-apt-repository ppa:webupd8team/java
apt-get update
apt-get install oracle-java8-installer
```

Let's enable UFW and allow ssh, plus elastic from TripAdvisor and the university :)
```
ufw allow 22/tcp
ufw enable

## From UCarleton
ufw allow from 134.117.249.0/24 to any port 9200

```


Then let's get the ES 1.7 package
```
curl -O https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.7.3.deb

dpkg -i elasticsearch-1.7.3.deb
```

We need to DISABLE clustering / multicast discovery
```
vi /etc/elasticsearch/elasticsearch.yml

## disable discovery.zen.ping.multicast.enabled
## set number of shards to 1, replication to 0


## then let's enable the service
update-rc.d elasticsearch defaults 95 10

```

Let's install some plugins
```
cd /usr/share/elasticsearch
bin/plugin install elasticsearch/marvel/latest
bin/plugin install royrusso/elasticsearch-HQ/v1.0.0
```
