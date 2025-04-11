# hello_haproxy_docker

Example to proxy 4 https websites over haproxy

* httpa://ww1.app.local > http://127.0.0.1:81
* httpa://ww2.app.local > http://127.0.0.1:82
* httpa://ww3.app.local > http://127.0.0.1:83
* httpa://foo.local > http://127.0.0.1:84

## Description

The docker-compose will start up 4 nginx servers with uniq ports.
The docker-compose will also start one haproxy what listens on 4 virtual domain names on port 80 and 443.
The haproxy will regargin to its mounted haproxy.cfg file then proxy it to its backend and handle https certificated
The certificates were issued by minica, a private self authority cert for testing and development purpose.



## Requirements
* working docker engine
* hosts entries on the host where the docker is running, example /etc/hosts
* 127.0.0.1 ww1.app.local ww2.app.local ww3.app.local foo.local
* the dockers/certs/minica.pem files needs to be imported into your browsers as authority certificate 

## Installation
```
git clone https://github.com/myridia/hello_haproxy_docker.git
cd hello_haproxy_docker/dockers
docker-compose up 
```
## Test 
* http://127.0.0.1:81
* http://127.0.0.1:82
* http://127.0.0.1:83
* http://127.0.0.1:84
* http://ww1.app.local
* http://ww2.app.local
* http://ww3.app.local
* http://foo.app.local
* https://ww1.app.local
* https://ww2.app.local
* https://ww3.app.local
* https://foo.app.local






