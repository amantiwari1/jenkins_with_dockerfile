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
RUN yum install java -y && yum install jenkins -y && yum install git -y
RUN echo -e "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers


CMD ["java", "-jar", "/usr/lib/jenkins/jenkins.war"]
````

lets make build image using dockerfile with web service (httpd)

```
$docker build -t webserver_image .
```
note: dot means current directory

launch jenkins image with port 

```
docker run -it --privileged -p 9999:8080 -v /:/host webserver_image
```

it will automatic show initialAdminPassword

```
Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

9cbf4390692345a9865661c47737d76a

This may also be found at: /root/.jenkins/secrets/initialAdminPassword
```
---
## Now we have job in Jenkins

first job 

create new job name is Job1



















