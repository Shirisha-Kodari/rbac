#  steps: 
create iam user
user need clster access .create polict to describe eks
we integrate with iam user and k8 role


first create role in k8
next we do role binding in k8
next we create iam user ex: suresh and also create role : roboshop-rainee and attche policy
iam user creation :

go to iam ->create user -<give name >->add to group select->create user

create policy:
click on policy->click on serice and select eks ->select read->describer clsyer sletct->add arn->go to clsuetr copy cluster arn give region name  and click on next

give policy name ->RoboshopEKSDescribe

add policy to user suresh

create one ec2 instance login that server for suersh server
create credentials for suresh to login server and check clster describe
user ->suresh

error: i forgot to mention name space in rolebinding then i getting erorr not create rolebindhing 

suresh want to auth to 

suresh need authenticate with k8 eks this ths intergare 

* kubectl get configmap aws-auth -n kube-system -o yaml 

   apiVersion: v1
data:
  mapRoles: |
    - rolearn: arn:aws:iam::547520640015:role/eksctl-roboshop-nodegroup-roboshop-NodeInstanceRole-hXMKCdsp6wIe
      groups:
      - system:bootstrappers
      - system:nodes
      username: system:node:{{EC2PrivateDNSName}}
kind: ConfigMap
metadata:
  creationTimestamp: "2026-07-18T09:04:08Z"
  name: aws-auth
  namespace: kube-system
  resourceVersion: "1124"
  uid: bf2d4aaa-3190-4c0a-8858-6c130b999642

this add to aws-auth.yaml 

edit aws auth configmap take map users and copy to aws-auth.yaml 
edit yhat file we add mapusers olny and remove system master and add roboshop tarinee 
and add suresh user arn 
aws-auth.yaml apply atfter check this 

kubectl get configmap aws-auth -n kube-system -o yaml
* install kubectl in suresh server 
* chmod +x kubectl
* sudo cp kubectl /usr/local/bin/kubectl
* aws eks update-kubeconfig --region us-east-1 --name roboshop
 it downloads the EKS cluster information from AWS and creates/updates the Kubernetes configuration file (~/.kube/config).

 It stores:

Cluster endpoint (API server URL)
Cluster certificate
Cluster name
Authentication method

Without this file, kubectl doesn't know:

Which cluster to connect to.
How to authenticate.
Where the Kubernetes API server is.

when you run kubectl 
Before connecting to Kubernetes, run the AWS CLI to generate an authentication token."

* aws sts get-caller-identity 

* user suresh now autenticate with clsuter robshop 
cat /home/ec2-user/.kube/config

here we obsreve when we send kubectl then check token clsuer name doing authentiaction 

now user add to eks system 


