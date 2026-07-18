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