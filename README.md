# Simple CI CD - Stack

Sumarry:
* [Description](#description)
* [Services Used](#services)
* [Getting Start](#getting-start)
* [Routing](#routing-urls)


<h3 id="description">Description</h3>
   This stacks provides a simple to create enviroment for deploy applications
   
<h3 id="services">Services:</h3>

* Traefik
    * A proxy reverse do delivery all services inside a specific url , avoinding use service:port
    * DockerHub Image: ***traefik:v2.2***
    * DockerHub Image url: https://hub.docker.com/_/traefik
    * Documentation : https://docs.traefik.io/
    
* Jenkins
    * To create pipelines of CI CD env
    * DockerHub Image: ***jenkins/jenkins:lts*** (custom) 
    * DockerHub Url: https://hub.docker.com/_/jenkins
    * Documentation : https://jenkins.io/doc/
    
* Nexus 
    * To store jars of java projects
    * DockerHub Image: ***sonatype/nexus3***
    * DockerHub Url: https://hub.docker.com/r/sonatype/nexus3
    * Documentation : https://help.sonatype.com/docs
        
* Portainer
    * To manage all containers in docker stack
    * DockerHub Image: ***traefik:v2.2***
    * DockerHub Url: https://hub.docker.com/r/portainer/portainer
    * Documentation : https://portainer.readthedocs.io/en/stable/

<h3 id="getting-start">Getting Start</h3>

Before to start services yout need create unversioned folders of projects, mapped in docker-compose for each project:

* jenkins/jenkins_home/
* nexus/nexus-data/
* portainer/portainer-data/
* sonar/sonar-data/

After create folder , enter each folder of projects and just need to execute command:
```bash
docker-compose up -d


#jenkins (only first execution)

docker-compose up -d --build 
```

<h3 id="routing-urls">Routing Urls</h3>
For Default Every project was configured to run in subfolder

* http://localhost:8080 (Traefik DashBoard)
* http://localhost/portainer/
* http://localhost/jenkins/
* http://localhost/nexus/
* http://localhost/sonarqube/


To change urls, each project have a second option that use a subdomain:
All docker-composer have a mark #subdomain , just remove it and commment PathPrefix.

Check documentation of Traefik Reverse Proxy Tool https://docs.traefik.io/routing/routers/