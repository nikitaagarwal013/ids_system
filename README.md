# Smart Intrusion detection system

## How to collaborate
* Clone the repo
* Create a new branch under your name
* Make your changes.
* Push into your branch.
* Make a pull request to merge it in master

## Navigation

* __bro_dev__: It has all  


## Useful Docker Commands

* docker images
  *
* docker ps -a: see all containers
* docker run -it -P anurag1591/bro_ids /bin/bash : -p to publish all exposed ports to random ports
* docker pull anurag1591/bro_ids
* docker rm $(docker ps -aq) : remove all containers
* docker stop $(docker ps -aq) : stop all containers
* docker rmi $(docker images -q) : remove all images
* docker ps -aq : List all containers
* docker ps --filter "status=exited" : Show only stopped containers
* Push images to docker cloud
  * export DOCKER_ID_USER="anurag1591"
  * docker login
  * docker tag my_image $DOCKER_ID_USER/my_image
  * docker push $DOCKER_ID_USER/my_image
* Build docker image from docker file
  * docker build -t anurag1591/bro_ids:1.1 -f /path/to/a/Dockerfile .
* Commit changes to docker images
  * sudo docker ps -l : get container id
  * sudo docker commit <container_id> new_image_name:tag_name(optional)
  * docker inspect <Commit hash> : View commit of using its hash
* docker start f357e2faab77 # restart it in the background
* docker attach f357e2faab77 # reattach the terminal & stdin


docker run --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.4.2

docker run --name kibana -p 5601:5601 -e "ELASTICSEARCH_URL=http://172.17.0.2:9200" docker.elastic.co/kibana/kibana:6.4.2

docker run -u 0 --name logstash -P -it --network host  docker.elastic.co/logstash/logstash:6.4.2 /bin/bash


logstash-plugin install logstash-output-kafka
