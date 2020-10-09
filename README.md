Tools used:

Repository- GitHub
Jenkins Pipeline - CI/CD
Maven - Build tool
Containerization - Docker for application Image
Nexus Artifactory - Private Repository for storing docker images
Helm Charts - Collection of files that describe a related set of Kubernetes resources
Monitoring - Promentheus for monitoring Docker containers and CADVISOR to expose promentheus matrix
Sonar Qube - Testing the jar file
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
