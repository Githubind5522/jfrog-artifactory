Deploying artifact into Jfrog from Jenkin and Downloading from Jfrog into Jenkin
==================================================================================

Jenkins Setup (t2 large instance):

    wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo

    sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io.key

    yum install jenkins -y

    yum install git maven java-1.8* -y

    sudo service jenkins start


Jfrog set up in another AWS instance
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

    ./artifactory.sh start  or sh artifactory.sh

Access artifactory from browser
==============================

    http://<PUBLIC_IP_Address>:8081 

Credentials
==========

    username: admin

    passord: password

in Jenkins server
=================

    >>> Add Artifactory plugin (its for Jfrog --Manage Jenkins--->Manage Plugin-->Search Arifactory in Available)

    >>> Provide the ip address of Jfrog and Server id called Jfrog (Manage Plugin -- Configure system):

![Capture](https://user-images.githubusercontent.com/54719289/104105373-94071000-52d3-11eb-94ac-e4f1d0c4b22f.JPG)

    >>> Provide the details of Git and Maven Tool configuration (Manage Jenkins -->Global onfiguration)

    >>> create a New Pipeline item called  jfrog-deploy and  place Jenkinsfile code in configure


After that build the project and see the result in console output:

![Capture](https://user-images.githubusercontent.com/54719289/104105137-3aeaac80-52d2-11eb-984b-a31da4b210e5.JPG)


Check Jfrog UI for the update:

![Capture](https://user-images.githubusercontent.com/54719289/104105098-f65f1100-52d1-11eb-86d7-22c5c15ae323.JPG)


in Jfrog Instance

![Capture](https://user-images.githubusercontent.com/54719289/104105412-e9432180-52d3-11eb-817f-0c754beccf59.JPG)


Jenkin Server:  (Downloaded from Jfrog into Jenkins under- through Script /tmp folder)
==============


![Capture](https://user-images.githubusercontent.com/54719289/104105489-78e8d000-52d4-11eb-9dc9-c1acbf9e5736.JPG)
