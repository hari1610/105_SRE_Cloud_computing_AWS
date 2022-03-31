# SRE Intro
## User Journey
### User experience
#### Cloud computing with AWS
##### AWS Services
- AWS has a govcloud just for the governments, no one else can use it

#### AWS ( Amazon web serives
- Cloud computing platform by Amazon
- offers content delivery services, data storage.

#### AWS global infrastructure?
- available in 26 regions
- 84 zones
#### SRE?
- An SRE is responsible for how the code is deployed
- reposible for testing the reliability of new features
- figure out how to automate features.
#### benefits of cloud computing
- on the cloud we only pay for what we use ( cost benefit).
- You can go global in minutes.
-  A lot of management cost if you set up the server yourself
-  Its virtually accessable.


#### Regions and availability zone
- regions are locations where the data centres are held
- One region must hace at least 2 availability zones (actual data centres).
- if anything happens to one availability zone other one is used
- If the traffic increases other availability zones are used ( auto-Scaling)

#### What are the four pillars of cloud computing?
- Ease of use
- flexibility
- robustness
- cost

#### What is CDN?
- CDN stands for content delivery network
- Stores data close to the users location (like Cache)
- provides faster loading

#### What are on premise, hybrid and public cloud?
##### on Prem
- Data centre is run by the company
- data is phyically stored by them
- most expensive out of the 3 options
- everything is managed by the company
##### hybrid
- The company uses private data centre as well as public cloud
- confidential datas are stored privately
- public data is stored on the cloud.
##### public cloud
- all the data is stored on a cloud service like AWS
- Very cost effective (only pay for what you use)
- cuts down on maintenance cost.
- all your data is public


## Process of making an AWS
![cloud computing](https://user-images.githubusercontent.com/26463206/159463185-e7780cbc-b452-48bb-9572-16804a571bad.PNG)

- pem file contains the security key. When a request is sent from local host, this key is used to see if you are authorised.
- ec2 instance is a virtual machine, you can set security groups to make it secure.

### how to launch an instance
- log into the aws website
- create new e2 instance
- select ubuntu 18
- choose an instance type
- set the network and subnet, enable public IP
- select storage size
- create a tag for key and value. E.g Name 105_devops_hari_nginx
- create your security group
- - create a SSH one for admin access only, source should be my IP
  - create a new Http for public access,source should be anywhere
- review and launch
- select the key pair and launch
- connect to instance through ssh client
- then update and upgrade the ubuntu vm
- and then add install nginx

### linux commands
```shell 
systemctl status nginx 
 ```
- to restart the service you use: 
```bash 
sudo systemctl start nginx 
```
- to stop its:
```bash 
sudo systemctl stop service_name_
```

- How to enable service(This will start the service to start at startup:):
```bash
sudo systemctl enable service_name
```
- how to install a package:
```bash
sudo apt-get install package_name -y
```
- how to remove a package:
```bash
sudo apt-get remove package_name -y
```
- how to install a package:
```bash
sudo apt-get remove package_name -y
```
- how to check all process:
```bash
top
```
- who am I?
```bash
uname
```
```bash
uname -a
```
-where am I?
```bash
pwd
```
-create a dir?
```bash
mkdir dir_name_
```
-how to check?
```bash
ls
```
```bash
ls -a
```
- how to create a file?
```bash
touch name_file
```
```bash
nano file_name
```
- how to check content of the file without going inside the file?
```bash
cat file_name
```
- how to copy a file and move to a different location?
```bash
cp file_name destination
```

- how to move a file and move to a different location?
```bash
mv file_name destination
```
- how to delete a folder?
```bash
rm -rf folder_name
```

### File permission
- how to check a file permission: 
```bash
ll
```
- change file permission 
```bash 
chmod required_permision file_name
```
- to make a file executable 
```bash
chmod +x filename.sh
```
- write `w` read `r`.
- where to find the permision codes:  https://chmod-calculator.com/
- code block
```bash
#!/bin/bash
# run update
sudo apt-get update -y

# run upgrades

sudo apt-get upgrade -y

# install nginx

sudo apt-get install nginx -y
# ensure its running

sudo systemctl start nginx

# enable nginx
sudo systemctl enable nginx

```
- change the file to exe `chmod +x provision.sh

### creating a script to automate topcat server
- allow port number 8080 on you ec2 instance
- then create a script:

```bash
#!/bin/bash

#install tomcat
sudo apt-get install tomcat9 -y

#start the tomcat
sudo systemctl start tomcat9

#enable tomcat
sudo systemctl enable tomcat9

#use port 8080
sudo ufw allow 8080/tcp
```
### Cloud computing
##### What is a VPC?

![a vpc](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Virtual_Private_Cloud_%28VPC%29.svg/1280px-Virtual_Private_Cloud_%28VPC%29.svg.png)
- VPC stands for virtual private cloud
- A private section of the AWS you control
- you can place AWS resources like databases and EC2 instances
- you also have control over who has access
##### What is internet gateway?
- it provides your vpc a route to the internet.
- it is horizontally scaled, redundant and highly available.
- allows communication between instances and the internet.
- only one IGW can be attached to a VPC at a time
- IGW cannot be detached if instances are running
##### what is route tables?
- contains a set of rules(routes) that determines where network traffic is directed.
- route table provides the connection between all your AWS resources
- decides which subnet the traffic has to go.
##### what is Nacls?
- stands for network access control list
- optional layer of security for your VPC
- firewall for controlling traffic to subnets
- lies between the route table and subnets
- by default all traffics are allowed in and out.
- rules are evaluated from lowest to highest
##### what is a subnet?
- its a sub-section of a network
- two types of subnet private and public
- a public subnet has a route to the internet but private doesn't
- a subnet has to be only in one availablilty zone
- EC2 instances reside inside a subnet
##### what is security group?
- are found on the instance level
- virtual firewall that controls the traffic for instances
- will evaluate all of the rules
##### How did you secure your app on the cloud?
- by setting a security group
- set which port is for private and which is for everyone.
- only allowing port 20 and 80
##### What are the outbound rules for security group by default? and why?
- sets all outbound traffic as allowed(any ports)
- only authorised ports can come in so you dont need to check on the way out
- the security group doesnt know what type of traffic our instances are going to send out
##### what is the command to kill a process in linux?
There are two ways to kill a process:
1. you can kill a process by ID:
```bash
kill SIGNAL PID
#example
kill 9 5462
```
2. you can also kill a process by name:
```bash
killall SIGNAL Name
#example
killall 9 chrome
```

![kill process](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/kill%20process.PNG)

### Monolith - n-tire - 2-tier & Microservices Architecture

![architexture](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/monolith%20and%20microservice.png)

##### Monolith - N-tier - 2-tier architecture
 - a monolithic is built on a single unit.
 - there are three major parts
 - a client UI
 - a server-side application
 - a database
 - simple but has limitations
 - heavy apps can slow down the start up time
 - need to redeploy everytime there is a update
 - challenging to upscale
 - useful for simple and lightweight apps

###### two-tier
- there is no business logic layer between the client and the server
- the UI layer runs on the client side while dataset layer gets executed and stored on server side.
###### N-tier
- The program is distributed amongst 3 or more computers in a distributed network.
- UI, business logic and databases are seperate
##### Microservices architecture
- everything is a service on a micro level
- allows business to scale up and add new features
- new services does not effect the old services
- each service/feature can be test independently
- the database is not on the front end
- expensive

#### what is scale out?
- moving sideways
- scaling sideways when the number of users increases
#### what is scale up?
- moving upwards
- increase the volume in the specs when the size of the instance is too big for the current one.

### SDLC
- stands for software development lifecycle
- the process of end to end product development

###### The stages are:
- Planning: Just an idea, only in someones head
- Designing: Writing out how the product will look and what it needs.
- Development: Develop an environment that works for all of us. i.e the linux instance we created implementing the design.
- Testing: Nothing goes to production without testing, The test must pass in order to go to the next stage, Beta versions can happen after testing to get feedback from the user.
- Staging: Its the holding area before the code gets deployed. The program is packaged and ready, just on hold till the release date. After staging the code is deployed.

### Github
-	One person reviewing is always the best.
-	Someone who is more knowledgeable should merge.
-	Git enter will tell you all the commands that can be performed on git
-	If you delete the .git file you need to reconnect to the github remote before pushing the code back to github.

### S3
- stands for simple storage system
- used in data back up - disaster recovery plan (DR)
- S3 is globally available 
- Highly Available, can be accessed from any region
- s3 glacier class is for infrequent data access. Dont need to access the data frequently.

steps for S3:
- install ec2 instance
- install required dependencies 
- AWSCLI - Python 3 & above - running ec2
- AWS access & secret keys
- To access them from local host you need ssh port 22.


### AWS CLI & S3
- update & upgrade

```bash
sudo apt update -y
sudo apt upgrade -y
```
- install python 3.7
```bash
sudo apt install python
```
- check python version
```bash
python --version
```
- set python as alias for python3
```bash
alias python=python3
```
- install pip3
```bash
sudo apt install python3-pip
```
- install awscli
```bash
sudo apt install awscli
python3 -m pip install awscli
```
#### accessing S3 from ec2
```bash
aws configure
```
- enter the creditional details
- creating a bucket
```bash
aws s3 mb s3://105-sre-hari
```
- move data from e2 to s3
```bash
aws s3 cp sre.txt s3://105-sre-hari
```
- download data from s3 to e2
```bash
aws s3 cp s3://105-sre-hari /home/ubuntu
```
- remove files from inside the bucket
```bash
aws s3 rm s3://105-sre-hari/sre.txt
```
- remove bucket
```bash
aws s3 rb s3://105-sre-hari
```
### Docker
![docker](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/docker.PNG)
- its a containerisation platform
- makes project immuteable and globally available
- there are other types such as  Crio, Rocket
##### virtualisation vs Docker

![doverVSVm](https://wiki.aquasec.com/download/attachments/2854029/docker-birthday-3-intro-to-docker-slides-18-638.jpg?version=1&modificationDate=1515522843003&api=v2)
- Virtual mahcines take up 50% of your hardware
- Docker shares the resources
- Docker only uses the resource it needs
- Docker can create its own volumes
- containers in Docker has its own volume
##### Installing docker on windows
- Download the docker desktop from their website
- follower the installer instructions to complete docker
- you might have to restart your pc couple of times
- run ```docker run hello-world``` on CLI to see if docker works

### Docker commands
- download an image
```bash
 docker run -d -p 80:80 hjalendran/sre_105_index_hari:latest
```
- list all the images
```bash
 docker images
```
- list all the running containers
```bash
 docker ps
```
- move files into a docker container using container id
```bash
 docker cp index.html b1c78ac9657f:/usr/share/nginx/html/index.html
```
- create a docker image from container
```bash
 docker commit b1c78ac9657f hjalendran/sre_105_index_hari
```
- push the image to the docker hub
```bash
 docker push hjalendran/sre_105_index_hari:latest
```
### Docker file to automate the process of building customised image - building a microservice with docker

- Create a Dockerfile in the same location as your project(Dockerfile has no extension)
![dockerfile](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/dockerfile.PNG)
- inside it decide which base image you are going to use. for example:
```bash
FROM nginx
```
- As an optional step you can set the author of the image. For example:
```bash
LABEL MAINTAINER=HARI
```
- copy the data from localhost to your container. For example:
```bash
COPY index.html /usr/share/nginx/html
```
- Set what is the required port for your project
```bash
EXPOSE 80

``` 
- launch the app using CMD. For ecample:
```bash
CMD ["nginx", "-g", "daemon off;"]
# -g allows the image to be accessed globally
``` 
- Finally build the image from the dockerfile. For example:
```bash
docker build -t hjalendran/105_sre_nginx_test .
#the . tells you the location you want the test to run from
```
- once it runs fine you can push it to docker hub. Example:
```bash
docker push hjalendran/105_sre_nginx_test:latest
```

### Making the Products Api on docker
- create a dockerfile in the same location as the api project
- Make swagger run outside development mode, by commenting out the if statement

![swagger](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/swagger.PNG)

- get the dotnet base image and creating a working directory.
```bash
COPY *.csproj ./
RUN dotnet restore
```
- The overall dockerFile:
```bash
# Get the base image for api
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /ProductsApiApp

#copy the cs project
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /ProductsApiApp
EXPOSE 80
COPY --from=build-env /ProductsApiApp/out .
ENTRYPOINT ["dotnet", "ProductsApiApp.dll"]
```

### Kubernetes
- also known as k8
- its a container orchestration system
- made by google
- allows you to scale your containers
- kubernetes is managed automatically once set by you

#### advantages of Kubernetes
- self healing
- load balancing and service Discovery
- aumated rollouts and rollback
- auto scaling
- automatic bin packing
- storage orchestration

#### kubernetes services
- deployments
- pods ( each pod has its own IP)

#### Kubernetes architecture
![kubernetes_Architecture_](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/kubernete_architecture.PNG)

#### how to install kubernetes
- open docker desktop
- go to settings
- click on kubernetes
- select enable kubernetes and show system containers.
- click apply and restart
- run `kubectl get service` to check everything is working properly

#### k8 commands
- To get a list of services
```bash
kubectl get service 
```
- To get a specific service
```bash
kubectl get service service_name_
```
- To see all deployment
```bash
kubectl get deploy 
```
- To see a specific deploy
```bash
kubectl get deploy deploy_name_ 
```
- To get a list of pods
```bash
kubectl get pod 
```
- to see details about a pod:
```bash
kubectl describe pod pod_name_
```
### YAML
- yaml is a scripting language
- they have a extension of .yml or .yaml
- To start a yml file you use three `---`
- yml is case sensitive
- intendation of yml is important
##### Use cases of Yaml
- Can be utilised with:
- - k8
- - docker-compose
- - ansible
- - cloud-formation
- To codify anything and everything in order to automate processess
#### To write a script
![kubernete-nginx](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/kubernete-nginx.png)


- create a folder called nginx-deploy

- create a file for nginx_deployment.yml
```yml
apiVersion: apps/v1 # which api to use for deployment
kind: Deployment # what kind of service/object you want to create

#what would you like to it - name the service/object
metadata:
  name: nginx-deployment # naming the deployment



spec:
  selector:
    matchLabels:
      app: nginx # look for this label to match with k8 service
  # Let's create a replica set of this with 2 instances/pods
  replicas: 3

  # template to use its label for k8 service to launch in the browser
  template:
    metadata:
      labels:
        app: nginx # This label connects to the service or any other k8 components

  # Let's define the container spec
    spec:
      containers:
      - name: nginx
        image: hjalendran/105_sre_nginx_test:latest
        ports:
        - containerPort: 80
```
- create a file for nginx_svc.yml
```yml
---

apiVersion: v1
kind: Service

# Metadata for name
metadata:
  name: nginx-svc
  namespace: default 

# Specification to include ports Selector to connect to the deployment
spec:
  ports:
  - nodePort: 30442 # range is 30000-32768
    port: 80
    protocol: TCP
    targetPort: 80

# Let's define the selector and label to connect to nginx deployment
  selector:
    app: nginx # this label connects this service to deployment
 # creating LoadBalncer type of deployment
  type: LoadBalancer
```
- now deploy your deployment file with:
```bash
kubectl create -f nginx-deploy.yml
```
- now deploy your service file with:
```bash
kubectl create -f nginx-service.yml
```
- now you should find nginx running on local host.
- To edit a service `kubectl edit`
### Best practice to scale out and adapt micro-services
- plan the architecture with a small team, test, learn and move on
- use Docker to containerise your apps for fast and consistent delivery
- orchestration with k8 to make your life easy

#### deploying my api on kubernetes
![test_api](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/test_api.png)
- Create a file to deploy the api image
```yml
apiVersion: apps/v1
kind: Deployment


metadata:
  name: api-test-deployment # naming the deployment



spec:
  selector:
    matchLabels:
      app: api-test
  replicas: 3
  template:
    metadata:
      labels:
        app: api-test # This label connects to the service or any other k8 components

  # Let's define the container spec
    spec:
      containers:
      - name: api-test
        image: hjalendran/apitest:latest
        ports:
        - containerPort: 80
```
- Create a file a service file to connect
```yml
---

apiVersion: v1
kind: Service

#Metadaa for name
metadata:
  name: api-test-svc
  namespace: default 

# Specification to include ports
spec:
  ports:
  - nodePort: 30442 # range is 30000-32768
    port: 90
    protocol: TCP
    targetPort: 80

#Let's define the selector and
  selector:
    app: api-test
 # creating LoadBalncer type of deployment
  type: LoadBalancer
```
- run both the deployment and service yml


### To make your API globally available
- test it on your localhost first
- find out the requuirements you need for the API:
- - Minimum requirement for hard and memory/EBS
  - linux ubuntu 18.04
  - docker installed
  - minimum single node k8 cluster running on ec2 (minikube)
  - T2medum
  - .net installed
  - storage to backup the data
  - how many containers?
- For Amazon EC2
  - T2 medium
  - required dependicies - Docker - k8 Minikube
  - Migrate the data - SCP/Rsycn
  - ubuntu 18.04
  - Ec2 - SG - to allow required traffic/ports
  - file.pem
  - minikube takes at least one cpu

### Installing minikube & running your Api
- log into the ubuntu virtual machine
- install kubectl first using the following command:

```bash

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

```
- now make kubectl executeble:
```bash
chmod +x ./kubectl

```
- now move kubectl:
```bash
sudo mv ./kubectl /usr/local/bin/kubectl
```
- now install Docker:
```bash
sudo apt-get install docker.io -y
```
- now install minikube and make the file executable and move it to the same location as kubectl
```bash
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```
- you can check if its installed properly by running:
```bash
minikube version
```
- your output should be something similar to this:
![minikube-version](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/minikube-version.png)
- now become a root user:
```bash
sudo -i
```
- kubernetes requires conntrack to be installed in the root path:
```bash
sudo apt install conntrack
```
- now start minikube with no driver:
```bash
minikube start --vm-driver=none
```
- now check the status to see everything is working
```
minikube status

```
![minikube-status](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/minikube_status.png)

- now copy in your yaml file for deployment and serive into the virtual machine
```bash
# option i makes sure you are not overwriting any existing files
scp -i [auth file] [source] [desitination]
# example:
$ scp -i ~/.ssh/105.pem api_test-service.yml ubuntu@ec2-52-19-104-232.eu-west-1.compute.amazonaws.com:
```
- now deploy both files using kubernetes, always run deploy first!:
```bash
kubectl create -f [filename]
# example:
kubectl create -f api_test-deploy.yml
kubectl create -f api_test-service.yml
```
- Run `kubectl get deploy` to get the access port for your api

![kube_service](https://github.com/hari1610/105_SRE_Cloud_computing_AWS/blob/main/images/kube_service.png)

- Now allow that port in your security group.

### stateless and stateful (Nacl and security group)
- Nacl is stateless and Security Group is stateful.
- stateless means that any changes applied to an incoming rule isn't automatically applied to an outgoing rule.
- Example: If a request comes through port 80, it should be explicitly indicated that its outgoing response would be the same port 80.
- stateful means that any changes which are applied to an incoming rule is automatically applied to a rule which is outgoing.
- Example: If the incoming port of a request is 80, the outgoing response of that request is also 80 (it is opened automatically) by default.