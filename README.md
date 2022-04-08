Repository to go along with the following tutorials: 

* *How to bootstrap Jenkins for disaster recovery and accountability* on the [master](https://github.com/tkgregory/jenkins-demo) branch 
([YouTube video](https://youtu.be/s7dw0ahriQY))
* *Building a Spring Boot application in Jenkins* on the [theme-park-job](https://github.com/tkgregory/jenkins-demo/tree/theme-park-job) 
branch ([YouTube video](https://youtu.be/sCcuUMn1vdM) | [article](https://tomgregory.com/building-a-spring-boot-application-in-jenkins/))
* *Building a Spring Boot application in Docker and Jenkins* on the [theme-park-job-docker](https://github.com/tkgregory/jenkins-demo/tree/theme-park-job-docker) branch
 ([YouTube video](https://youtu.be/Kc3Vw5vk1Lw) | [article](https://www.youtube.com/redirect?redir_token=E248KK1vOMl4QjSMqDmEO1Hq9Rl8MTU5MDM0MTg5NEAxNTkwMjU1NDk0&q=https%3A%2F%2Ftomgregory.com%2Fbuilding-a-spring-boot-application-in-docker-and-jenkins%2F&event=video_description&v=Kc3Vw5vk1Lw))
* *Deploying a Spring Boot application into AWS with Jenkins* on the [theme-park-job-aws](https://github.com/tkgregory/jenkins-demo/tree/theme-park-job-aws) branch
 ([YouTube video](https://youtu.be/5xh0nAYeZNc) | [article](https://www.youtube.com/redirect?q=https%3A%2F%2Ftomgregory.com%2Fdeploying-a-spring-boot-application-into-aws-with-jenkins%2F&v=5xh0nAYeZNc&event=video_description&redir_token=dGMvj5k7_gK1m_rEu4sZr2ug7D18MTU5MDM0MTk3OUAxNTkwMjU1NTc5))

## Running Jenkins

`./gradlew docker dockerRun`

Jenkins will then be available at [http://localhost:8080](http://localhost:8080).



#build docker image
docker build -t jenkins-demo .

#run docker image
docker run jenkins-demo


#list docker images and get the id of jenkins-demo
sudo docker ps -a


#connect to the image as root and start the shell
docker exec -it --user root d5e2877b9161 sh


#modify permissions on sock file to enable docker in docker
chmod 666 /var/run/docker.sock



#Running from gradle 
#go to the root directory of jenkins-demo
./gradlew docker dockerRun


#list the images of docker or use ps top get the list of currently running
docker images
docker ps


#connect to the container as root
docker exec -it --user root f60a333b56d1 sh


#modify permissions on sock file to enable docker in docker
chmod 666 /var/run/docker.sock


#connect to the container as non-root and run the following which should work 
docker ps


###INSTALLATION FROM SCRATCH###

#install new image without jdk
docker run -p 8080:8080 -p 50000:50000 -d -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts


#install new image with jdk
docker run -p 8080:8080 -p 50000:50000 -d -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11


#docker images 
sudo docker ps -a

#connect to the container as root
docker exec -it --user root <container id> sh

#install docker
curl https://get.docker.com/ > dockerinstall && chmod 777 dockerinstall && ./dockerinstall

#modify permissions on sock file to enable docker in docker
chmod 666 /var/run/docker.sock

#test docker daemon
docker ps

