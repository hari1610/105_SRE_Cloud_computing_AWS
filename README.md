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

- pem file contains the security key. When a request is sent from local host, this key is used to see if you are authorised.

### how to launch an instance
- log into the aws website
- create new e2 instance
- select ubuntu 18
- create your security group
- create one for ssh which will be for you or devs and create one for everyone.
- connect to instance through ssh client
- make sure you are on the same working directory as 105.perm
- copy the ssh key

![cloud computing](https://user-images.githubusercontent.com/26463206/159463185-e7780cbc-b452-48bb-9572-16804a571bad.PNG)

