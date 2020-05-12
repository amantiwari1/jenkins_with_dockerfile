# Lets make jenkins with dockerfile
 
 Installed required list in your system -
 1) Docker
 2) Jenkins
 3) Git
 
 want to know how to install...
 [Check out how to install Docker, Jenkins, Git](https://github.com/amantiwari1/git_jenkins_docker/blob/master/README.md)

# warning - this only work in rhel 8 OS!

first lets make create dir and after change directory web then create directory 'website' and create file 'Dockerfile'

```
$mkdir web

$cd web 

$mkdir website

$touch Dockerfile
```

Create Simple index.html in Website Folder

now,
need write code in dockerfile

should be likes this 

```
$vim Dockerfile
```
---
```
FROM centos

RUN yum install wget -y
RUN wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
RUN rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
RUN yum install java-11-openjdk -y
RUN yum install jenkins -y
RUN systemctl start jenkins 

EXPOSE 80

CMD cat /var/lib/jenkins/secrets/initialAdminPassword
````

lets make build image using dockerfile with web service (httpd)

```
$docker build -t webserver_image .
```
note: dot means current directory

check if docker launch in webserver_image is working or not 

```
docker run -dit --name web1 -p 8083:80  webserver_image
```








