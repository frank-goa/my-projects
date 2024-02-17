# Creating a Docker file and Docker Image for HTML application

## In this project we will create a Docker image of a HTML application and run it as a docker container

### Steps
- Create an EC2 instance
- SSH into the ec2 instance
- run these commands one at a time
```bash
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo docker ps
sudo apt install zip
sudo usermod -aG docker $USER
sudo init 6
systemctl status docker 
docker ps
docker images
```
- go to free-css.com
- click on a template of your choice
- right click on the download link
- copy link address
```bash
pwd
/home/ubuntu
mkdir my-website
cd my-website
wget https://www.free-css.com/assets/files/free-css-templates/download/page295/edgecut.zip
unzip edgecut.zip
cd edgecut-html/
cp -R * ../.
cd ..
rm -rf edgecut-html edgecut.zip
```
- we need to create a docker file from our application
- using this docker file we wil create the docker image
- with this docker image we can then run a container
- since our application is a HTML application which will run on HTTPD
- so in the docker file we will have to pull the image of HTTPD
- go to hub.docker.com and search for httpd
```bash
FROM httpd:2.4
COPY ./public-html/ /usr/local/apache2/htdocs/
```
- create a Dockerfile
- paste the foll content
```bash
FROM httpd:2.4
COPY . /usr/local/apache2/htdocs/
```
- create a docker image using this Dockerfile
```bash
$ docker build . -t my-website:latest
.......
Successfully built 071e032ad864
Successfully tagged my-website:latest

$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
my-website   latest    071e032ad864   About a minute ago   174MB
httpd        2.4       2776f4da9d55   4 weeks ago          167MB

$ docker run -d -p 80:80 my-website:latest
d0dedebde4c057b75c0eb7f8f01d8cf66683775068b74c2c77af031887c488ab

$ docker ps
CONTAINER ID   IMAGE               COMMAND              CREATED         STATUS         PORTS                               NAMES
d0dedebde4c0   my-website:latest   "httpd-foreground"   6 seconds ago   Up 5 seconds   0.0.0.0:80->80/tcp, :::80->80/tcp   nervous_raman

```
- in the security inboud rules of the ec2 instance, allow port 80
- copy the pulic ip address of your ec2 instance and access it in a browser on port 80
- your should be able to access your web application

