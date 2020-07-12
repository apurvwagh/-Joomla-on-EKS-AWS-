# Joomla-on-EKS-AWS-
Launch Joomla-on-EKS

Launching Joomla-on-EKS

1) Step1: Create EKS cluster and configure the kubeclt command for the launched cluster1

        #aws eks update-kubeconfig --name mycluster

2) Step2: Install Amazon EFS Utilities on every node in the cluster using following command:
          #yum install amazon-efs-utils

3) Step3: Create namespace for the task.

   #kubectl create namespace webns1

4)Step4: Create an EFS file system.on AWS GUI

5) Step5: In create-efs-provisioner.yaml file, replace the FILE_SYSTEM_ID at line no. 22 and replace the nfs server at line no. 33 with the values of your EFS file system


6) Step6: Create the EFS Provisioner, Role and Storage Class in the webns namespace using following commands:

         #kubectl create -f create-efs-provisioner.yaml -n webns1

         #kubectl create -f create-rbac.yaml -n webns1

         #kubectl create -f create-storage.yaml -n webns1

7) Step7: Run the kustomization.yaml file to setup the environment and deploy the Joomla to the EKS. Run the following command:

          #kubectl create -k .
8)  Step8: Now our Joomla site is deployed to the EKS and can be accessed using the EXTERNAL-IP provided by joomla service.

           #kubectl get all

Finally : open the EXTERNAL-IP provided by the service/joomla in the browser to view the deployed joomla site.

