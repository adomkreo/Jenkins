# Jenkins
1. first, create a volume, take note of the the name and make sure you are in the right zone.
2. the create a persistant volume claim, here too, take note of the name and storage class name which is the same as the volume name.
3. create a service account.
4. create a service
5. then create a deployment, make sure the last part, where the volume mounts name (produced after the persistant(volume) is created. this name can be different than the name passed.
6. also the caim name must be the same as created during persistantvolume claim.
7. go to aws route r3, create an a record, then deploy the ingress.
   important: once jenkinsis runing, use the following command to get the initial password:
   kubectl exec jenkins-55665945f9-c9ckg -n jenkins cat /var/jenkins_home/secrets/initialAdminPassword (pod name will ofcourse be different)

###################################################################################
###################################################################################



# Install jenkins on redhat.
create a ubuntu t2 medium redhat ec2 instance open port 22,8080, 80,443
run the following script:
#!/bin/bash
sudo timedatectl set-timezone America/New_York
sudo hostnamectl set-hostname jenkins
sudo yum install wget tree vim git nano unzip -y
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade -y
# Add required dependencies for the jenkins package
sudo yum install java-17-openjdk -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
echo "echo of jenkins installation"
sudo su - ec2-user
