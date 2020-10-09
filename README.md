Tools required for setup:

Repository- GitHub
Jenkins Pipeline - CI/CD
Maven - Bild tool
Containerization - Docker for application Image
Nexus Artifactory- Private Repository for storing docker images
Helm Charts-collection of files that describe a related set of Kubernetes resources
Monitoring- Promentheus for monitoring Docker containers and CADVISOR to expose promentheus matrix
Sonar Qube- Testing the jar file
Splunk - Log monitoring
AWS- VPC,Route53

Steps:

-->Developers will push the sourcecode in GitHub.
-->Once the code is commited in GitHub by developers, using WebHooks automatically start the Jenkins Pipeline. Groovy script is used in Jenkins Pipeline
-->Using Build tool Maven, The code is converted into Jar file using pom.xml file. Maven plugin has to be installed in jenkins
-->Simultaneously using docker file with jar details and required port exposure,create a Docker Image
-->The Docker images are kept in a private repository called Nexus artifactory.We have to create Docker Hosted Repository for storing the containers.
-->Docker Containers are monitored by Promentheus.Container Advisor(CADVISOR) is used to analyse and exposes resourse useage and performance data from running container.
-->Jar file which we got from Maven will be tested using SonarQube which is for continuous inspection of code quality with static analysis of code to detect bugs, code smells and security vulnarability.
-->Using Quality Gates, Only if the code will pass the given criteria and there shouldnt be any bugs and errors then only it will be moved to Production Environment.
-->For SonarQube we require all the data that will be loaded in RDS.












Kubernetes(EKS) - Use a K8s cluster for each environment
Git repository- Bitbucket
Jenkins - CI/CD
Docker - creating application image
Helm - charts needed for deployment
Monitoring - prometheus, grafana
ELK - Logging
Vouch proxy - handles the OAuth
AWS - eks cluster, route 53
Kong -  extends Nginx  for ingress controller and api gateway.
Setup:

Here , I will use single repository in bitbucket for each environment, to store source codes
then will use jenkins pipeline to build the jar using maven and update the version in each integration, based on tag.
create a docker file with the latest jar details with the required details for environment setup and port exposure.
create a docker image.
create a helm chart with docker image the properties , vvolume mounts , ports for jmx if required, the Chart.yaml will contain the latest version, values.yaml will contain all the properties needed .
Steps 4,5,6 can be automated and previous templates used for new services.
On K8 cluster we will clone the helm repo and update the changes to already deployed service if present, in rolling deployment.
For monitoring we can use prometheus do extract metrics and use grafana to create dashboard.
Alertmanger will be configured with prometheus , we can also use opsgenie wih alertmanger for alert notifications
for logging we will be using elk which will be routed from pods Kong ingress controller will be used as an api gateway and proxy to route traffic to specific services
we can use vouch proxy and oauth through google.
DIAGRAMS ATTACHED.

NOTE: Most of the tools mentioned here are open source , there are various other tools which can be used.
