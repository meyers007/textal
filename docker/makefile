VOLUME=-v elastic-data:/usr/share/elasticsearch/data
NAME=elast

clean:
	#docker container prune --force
	docker ps -a --filter status=exited --format {{.ID}} | xargs docker rm
	docker ps -a

pull:
	docker pull docker.elastic.co/elasticsearch/elasticsearch:7.9.1
	docker volume create elastic-data

run:
	#docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.9.1
	#docker run --name ${NAME} ${VOLUME} -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.9.1
	docker run ${VOLUME} -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.9.1
	docker ps -a 
	#docker exec -it ${NAME}  chown elasticsearch:elasticsearch /usr/share/elasticsearch/data

bash:
	docker run ${VOLUME} --rm --name ${NAME}  -it docker.elastic.co/elasticsearch/elasticsearch:7.9.1 bash 
	#docker run -v elastic-data:/usr/share/elasticsearch/data -it docker.elastic.co/elasticsearch/elasticsearch:7.9.1 bash 
	docker ps -a 

gbash:
	docker exec -it ${NAME}  bash 

stop:
	
cheatsheet:
	docker image ls
	docker ps -a
	docker stop <container-id>
