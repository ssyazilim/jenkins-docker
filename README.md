# jenkins-docker
docker-compose.yml file for a docker in docker installation jenkins/jenkins

[sudo mkdir jenkins_home] <br />
[sudo chown 1000:1000 jenkins_home] <br />
[sudo chown 1000:1000 /var/run/docker.sock] <br />
[sudo -E docker compose up -d --build] <br />
[sudo docker exec -it jenkins bash] <br />
[sudo docker --version] <br />

[sudo docker logs -f jenkins] <br/>
copy the admin password paste to the jenkins UI

