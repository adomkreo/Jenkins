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
