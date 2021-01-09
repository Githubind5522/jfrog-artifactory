Jenkins install in one Server:
wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo

sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io.key

yum install jenkins -y

yum install git maven java-1.8* -y

sudo service jenkins start


Jfrog set up in another server
==============================

Install Java
yum install java-1.8* -y 

Download Artifactory packages onto /opt/
========================================

For Latest version of Artifactory OSS download it from here https://jfrog.com/open-source/
For Older version of Artifactory OSS download it from here https://jfrog.bintray.com/artifactory/
For Latest version of Artifactory Pro download it from here https://jfrog.com/artifactory/

Extract artifactory tar.gz file
==============================

cd /opt 
wget https://jfrog.bintray.com/artifactory/jfrog-artifactory-oss-6.9.6.zip
unzip jfrog-artifactory-oss-6.9.6.zip

Start the services
==================

cd /opt/artifactory-oss-6.9.6/bin
./artifactory.sh start

Access artifactory from browser
==============================

http://<PUBLIC_IP_Address>:8081 

Credentials
==========
username: admin
passord: password

in Jenkins server
=================

Add the Plugin called Artifactory(under Manage Jenkins--->Manage Plugin-->Search in Available)

Next, Provide the ip address of Jfrog under Manage Plugin -- Configure system

![Capture](https://user-images.githubusercontent.com/54719289/104104953-23f78a80-52d1-11eb-9b38-2e8cdd2d801a.JPG)

Next , provide the details of Git and Maven Tool configuration (Manage Jenkins -->Global onfiguration)

Next create a New Pipeline item called  jfrog-deploy and  place Jenkinsfile code in configure

After that build the project and see the result in console output,

![Capture](https://user-images.githubusercontent.com/54719289/104105074-c7489f80-52d1-11eb-9586-ab1cd870e5b1.JPG)

![Capture](https://user-images.githubusercontent.com/54719289/104105137-3aeaac80-52d2-11eb-984b-a31da4b210e5.JPG)


Check Jfrog server for the update:

![Capture](https://user-images.githubusercontent.com/54719289/104105098-f65f1100-52d1-11eb-86d7-22c5c15ae323.JPG)


![Capture](https://user-images.githubusercontent.com/54719289/104105120-1c84b100-52d2-11eb-9593-222ab7579482.JPG)


Jenkin Server:  (Dwonloaded from Jfrog into Jenkins under /tmp folder)
==============

![Capture](https://user-images.githubusercontent.com/54719289/104105156-5786e480-52d2-11eb-9a51-af95c1e79a6d.JPG)



