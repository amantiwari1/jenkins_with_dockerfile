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

FROM centos
RUN yum install httpd -y
COPY website/ /var/www/html/
EXPOSE 80
CMD httpd - DFOREGROUND 
````

lets make build image using dockerfile with web service (httpd)

```
$docker build -t webserver_image .
```
note: dot means current directory







