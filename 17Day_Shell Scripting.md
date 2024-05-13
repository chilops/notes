---
title: 17Day_Shell Scripting
uuid: 3aa3bd3e-0f67-11ef-af7b-a6f126245c9e
version: 154
created: '2024-05-11T12:52:30+05:30'
tags:
  - shell
  - shellscripting
  - shellscript-roboshop
  - aws
---

***Topics:***

1. *<mark style="background-color:#f8d616;">Crontab- auto scheduler<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8d616;">Shellscripts optargs<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8d616;">To run script as normal commands<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8914d;">AWS instances, route 53 records automation Using AWS CLI<!-- {"backgroundCycleColor":"24"} --></mark>*

1. *<mark style="background-color:#f8d616;">Creating an access Key & Secret keys<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8d616;">Roboshop instances creation & creating/updating route53 records using Shellscripts<!-- {"backgroundCycleColor":"25"} --></mark>*

\

\

*<mark style="background-color:#f8914d;">**Crontab - auto scheduler - Its is used for scheduling scripts**<!-- {"backgroundCycleColor":"24"} --></mark>*

 

*Launch an instance & connect to it.*

 

![9e52e1f8-23a3-4427-a557-68b130ace377.png|623](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/9e52e1f8-23a3-4427-a557-68b130ace377.png) [^1]

 

![0f1ade8e-5c6a-4f6c-872c-ccc49c04a02c.png|699.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/0f1ade8e-5c6a-4f6c-872c-ccc49c04a02c.png) [^2]

 

 

***#**git clone* [*https://github.com/chilops/shellscripts.git*](https://github.com/chilops/shellscripts.git) 

```
cd shellscripts/
```

```
ls
```

 

![496ab141-9255-4e2f-b47c-53d35d766aa2.png|887.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/496ab141-9255-4e2f-b47c-53d35d766aa2.png) [^3]

 

```
mkdir -p /tmp/shellscript-logs
```

```
cd /tmp/shellscript-logs
```

 

*Creating some log files with different dates*

```
touch -d 20231201 user.log
touch -d 20240418 satya.log
touch -d 20240419 mitra.log
touch -d 20231202 user2.log
touch -d 20231202 user2.js
touch -d 20231202 cart.js
touch -d 20231202 shipping.java
 
```

 

![a5bfa378-327c-40a6-ac19-b413b85edd58.png|834.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/a5bfa378-327c-40a6-ac19-b413b85edd58.png) [^4]

 

[*Crontab.guru - The cron schedule expression generator*](https://crontab.guru/%23\*_\*_\*_\*_\*) 

 

```
crontab -e     --> to edit a crontab (below schedule runs every minute)
```

 

![5a155e7f-5951-4a01-87c2-efe04fa180bb.png|818](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/5a155e7f-5951-4a01-87c2-efe04fa180bb.png) [^5]

 

*Now every minute cronjob schedule runs and it deletes the .log files which are more than 14 days as shown below*

![51536f4a-2426-49e0-b6bb-4cd3a1d50ea6.png|887.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/51536f4a-2426-49e0-b6bb-4cd3a1d50ea6.png) [^6]

 

*--To check log info*

```
tail -f /var/log/cron   
```

![9ae2d9f0-9910-493e-9f98-12fb546028a2.png|883.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/9ae2d9f0-9910-493e-9f98-12fb546028a2.png) [^7]

 

 

 *<mark style="background-color:#f8914d;">**Shellscripts optargs**:<!-- {"backgroundCycleColor":"24"} --></mark>*

 

*greeting*

*sh greeting.sh -n <name> -w <wishes>*

 

*Script for optargs*

![1c317756-9245-4d44-9dc5-33222066bd4b.png|791](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/1c317756-9245-4d44-9dc5-33222066bd4b.png) [^8]

 

```
git status
```

```
git add . ; git commit -m "optargs"; git push origin main
```

```
git status
```

![3eb5b2eb-a7ae-42e1-af2e-3a6514c148e9.png|722](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/3eb5b2eb-a7ae-42e1-af2e-3a6514c148e9.png) [^9]

 

```
git pull
```

*Try different options as below*

```
sh 18.greeting.sh
```

```
sh 18.greeting.sh x
```

```
sh 18.greeting.sh -n satya
```

```
sh 18.greeting.sh -n satya -w "good evening"
```

 

![db0e5b1d-ff6c-4526-a428-d9d170e410f3.png|828.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/db0e5b1d-ff6c-4526-a428-d9d170e410f3.png) [^10]

 

 

*Assignment:*

![c40f3d54-b13d-46ac-a0d6-37dd84a5aec9.png|791.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/c40f3d54-b13d-46ac-a0d6-37dd84a5aec9.png) [^11]

 

![7ff8cb6a-f8d0-4bcc-9fc5-da23eb9f5aee.png|768.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/7ff8cb6a-f8d0-4bcc-9fc5-da23eb9f5aee.png) [^12]

 

 

*Outputs:*

![acb14b35-6a8a-4c54-addd-5b26b5a52007.png|845](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/acb14b35-6a8a-4c54-addd-5b26b5a52007.png) [^13]

![05ed665d-9a9c-4847-92ae-8b20abc087f1.png|859](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/05ed665d-9a9c-4847-92ae-8b20abc087f1.png) [^14]

 

*<mark style="background-color:#f8914d;">**To run script as normal commands**:<!-- {"backgroundCycleColor":"24"} --></mark>*

 

![127773de-734f-4378-8b2a-d0f2a167d60f.png|786](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/127773de-734f-4378-8b2a-d0f2a167d60f.png) [^15]

 

![8332400f-ee62-4a57-aa5d-9fcd3443f60d.png|725](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/8332400f-ee62-4a57-aa5d-9fcd3443f60d.png) [^16]

\

\

*<mark style="background-color:#f8914d;">**AWS instances, route 53 records automation: Using AWS CLI**<!-- {"backgroundCycleColor":"24"} --></mark>*

*------------------------------------------*

*1. we need to create ec2 instances*

*2. mongodb, mysql, shipping we are creating t3.small remaining t2.micro*

*3. creating route53 records, web public ip remaining private ip*

 

*IAM --> identity access management*

*-----------------------------------*

*Authentication --> username/password*

*Authorization*

 

*Authorization --> you need to have access to enter project bays*

 

*Roles --> permissions*

 

*Roles --> permissions*

*---------------*

*Team Manager --> super admin*

*Team Lead --> admin*

*Senior Engineers --> normal access*

*Trainee --> READ access*

 

 

*user == person --> username/password = authentication*

 

*Authorization*

*----------------*

*Role and permissions*

 

*user --> what is the role of user ? --> what are the permissions attached to that role*

 

*Permissions*

*-----------------*

*Nouns and Verbs*

 

*AWS --> EC2, VPC, Route53, CDN, IAM == AWS resources*

 

*Resource*

*-------------*

*web, cart, catalouge, hostedzone == nouns*

*create, update, read, delete == actions == verbs*

 

*Satya == trainee*

*EC2 --> Web --> READ*

 

*Madhu == Junior DevOps Engineer*

*EC2 --> WEB --> READ and UPDATE*

 

*Sanjay== Senior Engineer*

*EC2 --> WEB --> Create, READ, UPDATE*

 

*Mitra== TEAM Lead*

*EC2 --> WEB, CART, CATALOGUE, etc --> Create, READ, UPDATE*

 

*chilops--> TEAM Manager*

*EC2 --> WEB, CART, CATALOGUE, etc --> Create, READ, UPDATE and DELETE*

 

 

*Resources also should have access to access another resources*

*----------------------------------------------------------*

*Roles to resources*

 

 

![f88764f6-5a29-41b4-bd24-a534aafe63c4.png|835.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/f88764f6-5a29-41b4-bd24-a534aafe63c4.png) [^17]

 

![39605c21-abe2-4f4f-9c96-dafb8a362998.png|833.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/39605c21-abe2-4f4f-9c96-dafb8a362998.png) [^18]

 

![20e35a90-5ec3-4f09-8642-0869290e5173.png|842.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/20e35a90-5ec3-4f09-8642-0869290e5173.png) [^19]

 

![aeba2b5b-f5d0-498c-b597-9b5260567343.png|829.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/aeba2b5b-f5d0-498c-b597-9b5260567343.png) [^20]

 

*instance can create other instance*

 

*Ex: aws ec2 run-instances --image-id ami-03265a0778a880afb --instance-type t2.micro --security-group-ids sg-087e7afb3a936fce7*

 

![7e1f86e6-da46-44d8-8252-2855cd8d9ac2.png|859.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/7e1f86e6-da46-44d8-8252-2855cd8d9ac2.png) [^21]

 

 

*Creating  a user to give admin access (full access)*

![74d3c2a9-b86b-485b-b096-14764a31b8e9.png|808.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/74d3c2a9-b86b-485b-b096-14764a31b8e9.png) [^22]

 

![12402068-995f-468e-984d-aca488af97c5.png|877.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/12402068-995f-468e-984d-aca488af97c5.png) [^23]

 

![4bc090c0-73fd-4f02-b28c-645843c268de.png|872.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/4bc090c0-73fd-4f02-b28c-645843c268de.png) [^24]

\

*<mark style="background-color:#f8914d;">**Creating an access Key**<!-- {"backgroundCycleColor":"24"} --></mark>*

 

![b077eb73-5ddd-4f60-bff6-0f02353c17c4.png|911.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/b077eb73-5ddd-4f60-bff6-0f02353c17c4.png) [^25]

 

![058ae505-cc64-4516-872c-d256467fa9bb.png|847.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/058ae505-cc64-4516-872c-d256467fa9bb.png) [^26]

 

![d6ab7bc8-1aa5-4afd-8078-1a4cc6b4366e.png|837.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/d6ab7bc8-1aa5-4afd-8078-1a4cc6b4366e.png) [^27]

 

\

 

*1. create one user and gave admin access*

*2. create access keys*

 

```
aws configure
```

 

![8cc702c6-9c49-4657-929c-26d5e985bded.png|843.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/8cc702c6-9c49-4657-929c-26d5e985bded.png) [^28]

 

![4758c6e5-a031-4bde-b149-fcf590e69302.png|779](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/4758c6e5-a031-4bde-b149-fcf590e69302.png) [^29]

 

![9a980cbc-df51-43d5-bcc5-6535380b2ec1.png|887](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/9a980cbc-df51-43d5-bcc5-6535380b2ec1.png) [^30]

 

*Now creating an AWS instance*

```
aws ec2 run-instances --image-id ami-0f3c7d07486cad139 --instance-type t2.micro --security-group-ids sg-0c9db47e9b4d484b6
```

 

![838c61cf-2629-46a5-9bfc-0ea07c12ea28.png|923.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/838c61cf-2629-46a5-9bfc-0ea07c12ea28.png) [^31]

 

*New instance got created*

![d4ff756c-0572-43a3-9c95-6edd9e1e3463.png|941.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/d4ff756c-0572-43a3-9c95-6edd9e1e3463.png) [^32]

 

 

*In the above process there is a loop hole.. People who is having access to above instance then they can see credentials, so others can misuse*

 

*So now deleting a user - chilops which we created earlier*

 

![2dfb5f38-1db7-4a47-9d67-d309399bd0f8.png|861.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/2dfb5f38-1db7-4a47-9d67-d309399bd0f8.png) [^33]

 

 

*Now we are proceeding to create a Role to avoid above misuse*

 

![6cd38f51-e24a-40ea-a85c-a87746289103.png|829.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/6cd38f51-e24a-40ea-a85c-a87746289103.png) [^34]

 

 

*Now we can give adminaccess(full) or ec2fullaccess & Route52fullaccess*

![48014100-4ffc-4bbf-a269-e743654b13ba.png|869.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/48014100-4ffc-4bbf-a269-e743654b13ba.png) [^35]

 

![6dd77a85-dc6e-4238-a811-28b4df94bf26.png|849.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/6dd77a85-dc6e-4238-a811-28b4df94bf26.png) [^36]

 

![89f0817f-250b-4b54-b6ba-7d8629ebbb38.png|829.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/89f0817f-250b-4b54-b6ba-7d8629ebbb38.png) [^37]

 

![f29c5867-b871-440d-b274-60b6683b3733.png|823.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/f29c5867-b871-440d-b274-60b6683b3733.png) [^38]

 

![6ad5ece4-8380-4318-8368-fea892d42a82.png|832.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/6ad5ece4-8380-4318-8368-fea892d42a82.png) [^39]

 

![6daabf6b-f322-4ddb-b247-2ebd18840899.png|897.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/6daabf6b-f322-4ddb-b247-2ebd18840899.png) [^40]

 

![b4f98645-7340-4b3c-9abd-5f907208d6a1.png|827](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/b4f98645-7340-4b3c-9abd-5f907208d6a1.png) [^41]

 

 

*created role*

*attached permissions*

*named it*

 

*attach this role to instance...*

 

 ![2421c376-4ba0-40e3-9e15-d5dfebc745c2.png|542](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/2421c376-4ba0-40e3-9e15-d5dfebc745c2.png) [^42]

 

 

```
aws ec2 run-instances --image-id ami-0f3c7d07486cad139 --instance-type t2.micro --security-group-ids sg-0c9db47e9b4d484b6
```

![f739b882-3d26-4e17-a45f-9b7eedeeaf43.png|925.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/f739b882-3d26-4e17-a45f-9b7eedeeaf43.png) [^43]

 

*Now new EC2 instance created*

![981e9283-4f7b-4449-a3fc-56567ab0ff56.png|937.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/981e9283-4f7b-4449-a3fc-56567ab0ff56.png) [^44]

\

\

*<mark style="background-color:#f8914d;">**Roboshop instances creation & creating/updating route53 records using Shellscripts**:<!-- {"backgroundCycleColor":"24"} --></mark>*

 

*1. instance creation*

 

*aws ec2 run-instances --image-id ami-03265a0778a880afb --instance-type t2.micro --security-group-ids sg-087e7afb3a936fce7 --tag-specifications 'ResourceType=instance,Tags=\[{Key=Name,Value=production}\]'*

 

*2. mongodb, mysql, shipping t3.small otherwise t2.micro*

*3. we need ip address to create route53 record.*

 

 

*Script*

![a80479c1-3cc9-4296-a739-0b124e1ae05b.png|933.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/a80479c1-3cc9-4296-a739-0b124e1ae05b.png) [^45]

 

*Line 18 continuation*

![f2f567e2-4234-4223-85b0-fa6b0576f908.png|899.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/f2f567e2-4234-4223-85b0-fa6b0576f908.png) [^46]

 

```
git status
```

```
git add . ; git commit -m "instances & hosted zones creation"; git push origin main
```

```
git status
```

 

![01caed30-873f-4c4b-a44c-270b14a21c89.png|709.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/01caed30-873f-4c4b-a44c-270b14a21c89.png) [^47]

 

```
git clone https://github.com/chilops/Roboshop-shellscripts.git 
ls -l
cd Roboshop-shellscripts/
ls -l
git pull   --> if required
```

![80a649dd-fe53-4885-96cd-80e6bf438e7e.png|855.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/80a649dd-fe53-4885-96cd-80e6bf438e7e.png) [^48]

 

 *-- It creates new instances & creates route53 records aswell (web IP we need to change manually since its updates with private ip, we need to change as public IP in route53)*

```
sh roboshop.sh     
```

![027b4516-f6ed-4d12-b7e2-c7710c8960d3.png|827.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/027b4516-f6ed-4d12-b7e2-c7710c8960d3.png) [^49]

 

 

*Using script 11 instances launched as below.*

![4fdf4f33-c31e-4cee-8296-2f9e7c2547de.png|846.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/4fdf4f33-c31e-4cee-8296-2f9e7c2547de.png) [^50]

 

 

*Using script route53 records created.(web IP we need to change manually since its updates with private ip, we need to change as public IP in route53)*

 

![3f8f2e4c-d3f1-4179-a5cf-e484ef7a48a4.png|878.3333740234375](https://images.amplenote.com/3aa3bd3e-0f67-11ef-af7b-a6f126245c9e/3f8f2e4c-d3f1-4179-a5cf-e484ef7a48a4.png) [^51]

 

 

*improvements*

*---------------*

*if web, get public ip and create records*

*check if records already exists*

*if exists update*

*if not exist create*

\

[^1]: Name _
    V
    Instance ID
    Instance state
    A
    Instance type
    scripts
    i-06672f9cafdad5abf
    Pending
    t2.micro

[^2]: SuperPUTTY - 44.223.1.6
    File View Tools Help
    Protocol SSH
    Host 44.223.1.6
    Login
    Password
    Session
    chilops
    Commands
    .O\* g D
    44.223.1.6
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ \]

[^3]: \[ centosdip-172-31-16-165 \~ \]$ git clone https: //github. com/chilops/shellscripts.git
    Cloning into 'shellscripts'.
    remote: Enumeratiog objects: 90, done.
    remote: Counting objects: 100% (90/90), done.
    remote: Compressing objects: 100% (68/68), done.
    remote: Total 90 (delta 45), reused 66 (delta 21), pack-reused 0
    Receiving objects: 100% (90/90), 10. 46 KiB \| 10. 46 MiB/s, done.
    Resolving deltas: 100% (45/45), done.
    44 . 223.1.6 \| 172. 31.16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ cd shellscripts/
    44. 223.1.6 \| 172. 31. 16.165 \| t2.micro \| https: //github. com/chilops/shellscripts.git
    \[ centosdip-172-31-16-165 \~/shellscripts \]$ 1s
    01. hello-world. sh
    05. variables. sh
    09. install-mysql.sh 13. install-packages. sh
    17. disk-usage. sh
    02 . variables. sh
    06. datatypes . sh
    10 . functions . sh
    14. without-exit-status . sh
    mail . sh
    03 . variables . sh
    07. arrays . sh
    11 . logs . sh
    15 . Delete-old-log. sh
    template. html
    04 . variablesArgs. sh
    08 . conditions . sh
    12 . loops . sh
    16. ifs. sh
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| https: //github. com/chilops/shellscripts.git
    \[ centos@ip-172-31-16-165 \~/shellscripts \]$ /

[^4]: \[ centosdip-172-31-16-165 \~/shellscripts \]$ mkdir -p /tmp/shellscript-logs
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| https: //github. com/chilops/shellscripts.git
    \[ centos@ip-172-31-16-165 \~/shellscripts \]$ cd /tmp/shellscript-logs
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20231201 user . log
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20240418 satya. log
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20240419 mitra. log
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20231202 user2. log
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20231202 user2.js
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20231202 cart. js
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20231202 shipping. java
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ \[\]

[^5]: \* \* sh /home /centos/shellscripts/15 . Delete-old-log. sh

[^6]: 44. 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ touch -d 20231201 user .log
    44 . 223.1.6 \| 172. 31.16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 /tmp/shellscript-logs \]$ 1s
    cart. js mitra. log satya. log shipping . java user2.js user . log
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 /tmp/shellscript-logs \]$ 1s
    cart. js mitra. log satya. log shipping . java user2. js

[^7]: \[ centos@ip-172-31-16-165 /tmp/shellscript-logs \]$ tail -f /var/log/cron
    Apr 23 04:38:01 ip-172-31-16-165 CROND \[4778\]: (centos) CMD (sh /home/centos/shellscripts/15. Delete-old-log. sh)
    Apr 23 04:38:01 ip-172-31-16-165 CROND \[4776\]: (centos) CMDOUT (Deleting file: /tmp/shellscript-logs/user . log)
    Apr 23 04:38:01 ip-172-31-16-165 CROND \[ 4776\]: (centos)
    CMDOUT (Deleting file: /tmp/shellscript-logs/user2. log)
    Apr 23 04:39:01 ip-172-31-16-165 CROND \[4797\]: (centos) CMD (sh /home/centos/shellscripts/15. Delete-old-log. sh)
    Apr 23 04:39:01 ip-172-31-16-165 CROND \[ 4796\]: (centos)
    CMDOUT (Deleting file: /tmp/shellscript-logs/user . log)
    Apr 23 04:40:01 ip-172-31-16-165 CROND \[4808\]: (centos) CMD (sh /home/centos/shellscripts/15. Delete-old-log. sh)
    Apr 23 04:40:01 ip-172-31-16-165 CROND \[ 4806\]: (centos) CMDOUT (Deleting file: )
    Apr 23 04:40:01 ip-172-31-16-165 CROND \[4822\]: (root) CMD (sh -x /boot/idle. sh &>/tmp/idle. out)
    Apr 23 04:41:01 ip-172-31-16-165 CROND \[ 4842\] :
    (centos) CMD (sh /home/centos/shellscripts/15. Delete-old-log. sh)
    Apr 23 04:41:01 ip-172-31-16-165 CROND \[ 4841\] :
    (centos) CMDOUT (Deleting file: )
    Apr 23 04:42:01 ip-172-31-16-165 CROND \[ 4848 \] :
    (centos) CMD (sh /home/centos/shellscripts/15. Delete-old-log. sh)
    Apr 23 04:42:01 ip-172-31-16-165 CROND \[ 4847\] : (centos)
    CMDOUT (Deleting file: )

[^8]: shellscripts > $ 18.greeting.sh
    1
    2
    #! /bin/bash
    3
    4
    NAME= " "
    5
    WISHES="Good Morning"
    6
    7
    USAGE ( ) {
    18
    echo "USGAE : : $(basename $0) -n <name> -w <wishes>"
    9
    echo "Options: : "
    OT
    echo " -n, Specify the name (mandatory)"
    11
    echo " -w, Specify the wishes. (Optional). Default is Good Morning"
    12
    echo " -h, Display Help and exit"
    13
    14
    15
    while getopts ": n:w:h" opt; do
    16
    case $opt in
    17
    n) NAME="$OPTARG"; ;
    18
    w) WISHES="$OPTARG"; ;
    19
    \\?) echo "invalid options: -"$OPTARG"" >&2; USAGE; exit; ;
    20
    :) USAGE; exit; ;
    21
    h) USAGE; exit; ;
    22
    esac
    23
    done
    24
    25
    #if \[ -z "$NAME" \] \| \| \[ -z "$WISHES" \]; then
    26
    if \[ -z "$NAME" \]; then # now wishes is optional
    27
    #echo "ERROR: Both -n and -w are mandatory options."
    28
    echo "ERROR: -n is mandatory."
    29
    USAGE
    30
    exit 1
    31
    fi
    32
    33
    echo "Hello $NAME. $WISHES. I have been learning Shell Script."
    34

[^9]: Untracked files:
    (use "git add <file>..." to include in what will be committed)
    18. greeting. sh
    nothing added to commit but untracked files present (use "git add" to track)
    PS E: \\AWSDevops\\Repos \\shellscripts> git add . ; git commit -m "optargs; git push origin main

[^10]: centos@ip-172-31-16-165 \~/shellscripts \]$ sh 18. greeting. sh
    ERROR: -n is mandatory.
    USGAE: : 18. greeting. sh -n <name> -w <wishes>
    Options: :
    -n, Specify the name (mandatory)
    -w, Specify the wishes. (Optional) . Default is Good Morning
    -h, Display Help and exit
    44 . 223.1.6 \| 172. 31.16.165 \| t2.micro \| https://github. com/chilops/shellscripts.git
    \[ centosdip-172-31-16-165 \~/shellscripts \]$ sh 18. greeting. sh x
    ERROR: -n is mandatory.
    USGAE: : 18 . greeting. sh -n <name> -w <wishes>
    Options : :
    -n, Specify the name (mandatory)
    -w, Specify the wishes. (Optional) . Default is Good Morning
    -h, Display Help and exit
    44 . 223.1.6 \| 172. 31.16.165 \| t2.micro \| https: //github. com/chilops/shellscripts.git
    \[ centos@ip-172-31-16-165 \~/shellscripts \]$ sh 18. greeting. sh n
    ERROR: -n is mandatory.
    USGAE: : 18 . greeting. sh -n <name> -w <wishes>
    Options : :
    -n, Specify the name (mandatory)
    -w, Specify the wishes. (Optional) . Default is Good Morning
    -h, Display Help and exit
    44. 223.1.6 \| 172. 31.16.165 \| t2.micro \| https: //github.com/chilops/shellscripts.git
    \[ centosdip-172-31-16-165 \~/shellscripts \]$ sh 18.greeting. sh -n satya
    Hello satya. Good Morning. I have been learning Shell Script.
    44. 223.1.6 \| 172. 31. 16.165 \| t2.micro \| https: //github. com/chilops/shellscripts.git
    \[ centosdip-172-31-16-165 \~/shellscripts \]$ sh 18.greeting. sh -n satya -w "good evening"
    Hello satya. good evening. I have been learning Shell Script.

[^11]: shellscripts > $ 19.oldlogs-optargs.sh
    #! /bin/bash
    -VARIABLE-
    SOURCE_DIR=" "
    VOUAWN
    DESTINATION_DIR=""
    DAYS=14
    MEMORY= " "1
    ACTION=" "
    9
    10
    \* \*#-
    USAGE FUNCTOIN USED TO DISPLAY
    11
    USAGE ( ) {
    12
    echo "COMMAND USAGE: : $(basename $0) -s <Source Directory> -d <Destination Directory> -a <action: delete or archive> -t <No. of Days
    13
    echo "Options :
    14
    echo " -s: Specify the source directory"
    15
    echo "
    -d: Specify the destination directory when -a is archive"
    16
    echo " -t: Number of days back to delete log file"
    17
    echo " -m: Memory size of the file to delete log file"
    18
    echo " -a: Action to be performed on log files. Options : Delete or Archive"
    19
    echo " -h: Display Help and exit"
    20
    21
    22
    23
    \* \*# - -
    -OPT ARGS-
    24
    while getopts " : s:d: t:m:a:h" opt;
    25
    do
    26
    case $opt in
    27
    s ) SOURCE_DIR="$OPTARG"; ;
    28
    d)
    DESTINATION_DIR="$OPTARG"; ;
    29
    t)
    DAYS="$OPTARG"; ;
    30
    m) MEMORY="$OPTARG"; ;
    31
    a)
    ACTION="$OPTARG"; ;
    32
    h) USAGE; exit; ;
    33
    \\?) echo "Invalid Options: -"$OPTARG"" >$2; USAGE; exit; ;
    34
    esac
    35
    done
    36
    37
    - -CHECKING ACTION ARGUMENT PROVIDED OR NOT - - - -
    38
    39
    if \[ -z "$ACTION" \]
    40
    then
    41
    echo "ERROR: : -a option is mandatory. Either Delete or Archive"
    42
    exit 1
    43
    fi
    44

[^12]: 44
    45
    \* \*#-
    -CHECKING DESTINATION DIR PROVIDED IF ARCHIVE OPTION CHOOSEN-
    46
    47
    if \[ -z "$DESTINATION_DIR" \] && \[ "$ACTION" == "arcive" \]
    48
    then
    49
    echo "ERROR: : -d option is mandatory when -a is archive"
    50
    exit 1
    51
    fi
    52
    53
    if \[ ! -d $SOURCE_DIR \] # ! denotes opposite
    54
    then
    55
    echo "Source directory: $SOURCE_DIR does not exists."
    56
    fi
    57
    58
    -DELETE/ARCHIVE ACTION
    \* \*
    59
    60
    if \[ "$ACTION"=="delete" \]
    61
    then
    62
    FILES_TO_DELETE=$(find $SOURCE_DIR -type f -mtime +"$DAYS" -name "\*.log")
    63
    64
    while IFS= read -r line
    65
    do
    66
    echo "Deleting file: $line"
    67
    rm -rf $line
    68
    done <<< $FILES_TO_DELETE
    69
    else
    70
    FILES_TO_ARCHIVE=$(find $SOURCE_DIR -type f -mtime +"$DAYS" -name "\*.log")
    71
    72
    while IFS= read -r line
    73
    do
    74
    echo "Archiving file: $line"
    75
    zip -r "$DESTINATION_DIR/$(basename "$line") . zip"
    76
    rm -rf $line
    77
    done <<< $FILES_TO_ARCHIVE
    78
    fi

[^13]: 54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https://github. com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$ sudo sh 25-delete-oldlogs-optargs. sh
    ERROR: : -a option is mandatory. Either Delete or Archive
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https://github. com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$ 1
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https://github. com/knbob/shell.git
    centosdip-172-31-95-118 \~/shell \]$ sudo sh 25-delete-oldlogs-optargs . sh
    ERROR:: -a option is mandatory. Either Delete or Archive
    ERROR: : -s option is mandatory. Eg. /home/centos/shell-logs
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https: //github. com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$
    54 . 226.1.131 \| 172.31.95.118 \| t2.micro \| https://github.com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$ sh 25-delete-oldlogs-optargs. sh -s /home/centos/shell-logs/ -a delete
    Deleting file: /home/centos/shell-logs/user . log
    Deleting file: /home/centos/shell-logs/cart . log
    Deleting file: /home/centos/shell-logs/payment . log
    54 . 226.1.131 \| 172. 31. 95.118 \| t2.micro \| https://github. com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$
    54 . 226.1.131 \| 172. 31. 95.118 \| t2.micro \| https: //github.com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$ sh 25-delete-oldlogs-optargs. sh -s /home/centos/shell-logs/ -a delete
    Deleting file: /home/centos/shell-logs/user . log
    Deleting file: /home/centos/shell-logs/cart . log
    Deleting file: /home/centos/shell-logs/payment . log
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https: //github. com/knbob/shell.git
    centos@ip-172-31-95-118 \~/shell \]$ cd . ./shell-logs/
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| null
    centos@ip-172-31-95-118 \~/shell-logs \]$ 1s -la
    total 0
    drwxrwxr-x
    2 centos centos
    60 Dec 23 01:54
    drwx--
    5 centos centos 144 Dec 23 01:54
    rw-rw-r--
    1 centos centos
    0 Dec
    1 00:00 cart . js
    rw-rw-r--
    1 centos centos
    0 Dec 23 01:47 catalogue . log
    rw-rw-r--
    1 centos centos
    0 Dec
    1 00:00 payment . py

[^14]: 54 . 226.1. 131 \| 172. 31.95.118 \| t2.micro \| null
    \[ centos@ip-172-31-95-118 \~/shell-logs \]$ 1s -la
    total 0
    drwxrwxr-x 3 centos centos 136 Dec 23 02:15
    drwx-
    5 centos centos 144 Dec 23 02:15
    rw-rw-r--
    1 centos centos
    0 Dec 18 00:00 cart . log
    rw-rw-r--
    centos centos
    0 Dec 1 00:00 java . log
    drwxrwxr-x
    2
    centos centos
    6 Dec 23 02:14 sample
    rw-rw-r--
    1 centos centos
    0 Dec 22 00:00 shipping . log
    -rw-rw-r--
    1
    centos centos
    0 Dec 10 00:00 shipping . py
    -rw-rw-r--
    1
    centos centos
    0 Dec 1 00:00 user . log
    -rw-rw-r--
    1 centos centos
    0 Dec 10 00:00 web . log
    -rw-rw-r--
    1 centos centos
    0 Dec 22 00:00 web . py
    54 . 226.1.131 \| 172.31. 95.118 \| t2.micro \| null
    \[ centos@ip-172-31-95-118 \~/shell-logs \]$ cd . ./shell
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https: //github. com/knbob/shell.git
    \[ centos@ip-172-31-95-118 \~/shell \]$ sh 25-delete-oldlogs-optargs. sh -a delete -s /home/centos/shell-logs/ -t 5
    days : 5
    Deleting file: /home/centos/shell-logs/user . log
    Deleting file: /home/centos/shell-logs/java. log
    Deleting file: /home/centos/shell-logs/web . log
    54 . 226.1.131 \| 172. 31.95.118 \| t2.micro \| https://github. com/knbob/shell.git
    \[ centosdip-172-31-95-118 \~/shell \]$ sh 25-delete-oldlogs-optargs. sh -a delete -s /home/centos/shell-logs/ -t 5
    days : 5
    Deleting file:

[^15]: \[ centos@ip-172-31-42-78 \~/shell-script \]$ echo $PATH
    /home/ centos/ . local/bin: /home/centos/bin: /usr/local/sbin: /usr/local/bin: /usr/sbin: /usr/bin
    50 . 19. 197.9 \| 172. 31. 42.78 \| t2.micro \| https: / /github. com/daws-76s/shell-script. git
    \[ centos@ip-172-31-42-78 \~/shell-script \]$ sudo cp 18-greeting. sh /usr/local/bin/greeting
    50 . 19. 197.9 \| 172. 31. 42.78 \| t2.micro \| https: / /github. com/daws-76s/shell-script. git
    \[ centos@ip-172-31-42-78 \~/shell-script \]$ sudo chmod +x /usr/local/bin/greeting
    50. 19.197.9 \| 172. 31. 42.78 \| t2.micro \| https: / /github.com/daws-76s/shell-script. git
    \[ centos@ip-172-31-42-78 \~/shell-script \]$ cd

[^16]: \[ rootip-172-31-42-78 \~ \]# greeting
    ERROR: -n is mandatory
    USGAE: : greeting -n <name> -w <wishes>
    Options : :
    -n, Specify the name (mandatory)
    -W ,
    Specify the wishes. (Optional) . Default is Good Morning
    -h, Display Help and exit
    50 . 19. 197.9 \| 172. 31. 42.78 \| t2.micro \| null
    \[ root@ip-172-31-42-78 \~ \]# greeting -n sivakumar -w "Good Evening"
    Hello sivakumar. Good Evening. I have been learning Shell Script.
    50 . 19. 197.9 \| 172. 31. 42.78 \| t2.micro \| null
    \[ root@ip-172-31-42-78 \~ \]#

[^17]: \[ centos@ip-172-31-42-78 \~ \]$ aws s3 1s
    Unable to locate credentials. You can configure credentials by running "aws configure".
    50. 19.197.9 \| 172. 31. 42.78 \| t2.micro \| null
    \[ centos@ip-172-31-42-78 \~ \]$ aws ec2 run-instances --image-id ami-03265a0778a880afb --instance-type t2.micro --security-group-ids sg-0
    87e7afb3a936fce7
    Unable to locate credentials. You can configure credentials by running "aws configure"

[^18]: VPC
    CO RDS
    $3
    Elastic Kubernetes Service
    CloudFormation
    Route 53
    EFS
    IAM
    D EC2
    Identity and Access
    X
    IAM > Dashboard
    Management (IAM)
    IAM Dashboard
    C
    Q Search IAM
    Security recommendations
    C
    AWS Account
    Dashboard
    A Add MFA for root user
    Account ID
    Add MFA
    Access management
    Add MFA for root user - Enable multi-factor authentication (MFA) for the root user to improve security
    7 315069654700
    for this account.
    User groups
    Account Alias
    Users
    Root user has no active access keys
    joindevops Edit \| Delete
    Roles
    Using access keys attached to an IAM user instead of the root user improves security.
    Sign-in URL for IAM users in this account
    Policies
    https://joindevops.signin.aws.amazon.com/co
    Identity providers
    nsole
    Account settings
    IAM resources
    C
    Resources in this AWS Account
    Access reports
    Quick Links
    Access Analyzer
    User groups
    Users
    Roles
    Policies
    Identity
    External access
    providers
    My security credentials
    Unused access
    0
    2
    21
    2
    4
    Manage your access keys, multi-factor
    authentication (MFA) and other credentials.
    Analyzers and settings
    Credential report
    Organization activity
    What's new CZ
    View all

[^19]: Identity and Access
    X
    IAM > Roles
    Management (IAM)
    Roles (21) Info
    G
    Delete
    Create role
    Q Search IAM
    An IAM role is an identity you can create that has specific permissions with credentials that are valid for short durations. Roles can be assured by entities that you trust.
    Q Search
    <
    1 2 >
    Dashboard
    Role name
    Trusted entities
    Last activity
    Access management
    O
    AWSServiceRoleForAmazonEKS
    AWS Service: eks (Service-Linked Rol
    22 days ago
    User groups
    AWSServiceRoleForAmazonEKSNodegroup
    AWS Service: eks-nodegroup (Service 24 days ago
    Users
    Roles
    O
    AWSServiceRoleForAmazonElasticFileSystem
    AWS Service: elasticfilesystem (Servi. 32 days ago
    Policies
    0
    AWSServiceRoleForApplicationAutoScaling_DynamoDBTable
    AWS Service: dynamodb.application- 21 minutes ago
    Identity providers
    AWSServiceRoleForAutoScaling
    AWS Service: autoscaling (Service-Lit 24 days ago
    Account settings
    AWSServiceRoleForBackup
    AWS Service: backup (Service-Linke
    19 hours ago
    Access reports
    Access Analyzer
    AWSServiceRoleForEC2Spot
    AWS Service: spot (Service-Linked Rc
    External access
    0
    AWSServiceRoleForECS
    AWS Service: ecs (Service-Linked Rol
    181 days ago
    Unused access
    AWSServiceRoleForElasticLoadBalancing
    AWS Service: elasticloadbalancing (S 25 days ago
    Analyzers and settings
    Credential report
    AWSServiceRoleForGlobalAccelerator
    AWS Service: globalaccelerator (Serv

[^20]: Services
    Search
    \[Alt+S\]
    Global
    joindevops
    VPC
    CO RDS
    Elastic Kubernetes Service
    red CloudFormation
    fail Route 53
    FFS A-1 1AM
    Q Filter service or use case
    Step
    S
    Select trusted entity
    Commonly used services
    EC2
    Step 2
    Add permissions
    Lambda
    Other services
    Step 3
    Amazon EMR Serverless
    Web identity
    Name, review, and create
    Allows users federated by the
    Amazon OpenSearch Service
    a 3rd
    specified external web identity
    lis
    provider to assume this role to
    AmazonGrafana
    perform actions in this account.
    Amplify
    API Gateway
    O
    AppFabric
    ons
    Application Auto Scaling
    Application Discovery Service
    Application Migration Service
    AppStream 2.0
    AppSync
    AWS Backup
    Choose a service or use case
    Cancel
    Next

[^21]: Add permissions
    Choose one or more policies to attach to your new role.
    Filter by Type
    Step 3
    Name, review, and create
    Q ec2
    X
    All types
    30 matches
    <
    1
    2 >
    -
    Policy name \[
    Type
    Description
    0
    + AmazonEC2ContainerRegistryFullAccess
    AWS managed
    Provides administrative access to Ama...
    0
    AmazonEC2ContainerRegistryPowerUser
    AWS managed
    Provides full access to Amazon EC2 Co...
    0
    AmazonEC2ContainerRegistryReadOnly
    AWS managed
    Provides read-only access to Amazon E...
    0
    AmazonEC2Container ServiceAutoscale...
    AWS managed
    Policy to enable Task Autoscaling for A...
    0
    AmazonEC2ContainerServiceEventsRole
    AWS managed
    Policy to enable CloudWatch Events fo...
    0
    AmazonEC2ContainerServiceforEC2Role
    AWS managed
    Default policy for the Amazon EC2 Rol...
    AmazonEC2ContainerServiceRole
    AWS managed
    Default policy for Amazon ECS service ...
    AmazonEC2FullAccess
    AWS managed
    Provides full access to Amazon EC2 via...
    O
    AmazonEC2ReadOnlyAccess
    AWS managed
    Provides read only access to Amazon E...
    O
    AmazonEC2RoleforAWSCodeDeploy
    AWS managed
    Provides EC2 access to $3 bucket to do...
    0
    AmazonEC2RoleforAWSCodeDeployLi...
    AWS managed
    Provides EC2 limited access to S3 buck...
    AmazonEC2RoleforDataPipelineRole
    AWS managed
    Default policy for the Amazon EC2 Rol...
    n
    AmazonEC2 RoleforSSM
    AWS managed
    This policy will soon be deprecated PI

[^22]: IAM > Users > Create user
    Step 1
    Specify user details
    Specify user details
    Step 2
    Set permissions
    User details
    Step 3
    User name
    Review and create
    chilops
    The user name can have up to 64 characters. Valid characters: A-Z, a-z, 0-9, and + = , . @ _ - (hyphen)
    Provide user access to the AWS Management Console - optional
    If you're providing console access to a person, it's a best practice \[ to manage their access in IAM Identity Center.
    If you are creating programmatic access through access keys or service-specific credentials for AWS CodeCommit or Amazon Keyspaces, you can generate them after you create
    this IAM user. Learn more \[
    Cancel
    Next

[^23]: IAM > Users > Create user
    Step 1
    Specify user details
    Set permissions
    Add user to an existing group or create a new one. Using groups is a best-practice way to manage user's permissions by job functions. Learn more \[
    Step 2
    Set permissions
    Permissions options
    Step 3
    Review and create
    Add user to group
    O Copy permissions
    Attach policies directly
    Add user to an existing group, or create a new group. We
    Copy all group memberships, attached managed policies,
    Attach a managed policy directly to a user. As a best
    recommend using groups to manage user permissions by
    and inline policies from an existing user.
    practice, we recommend attaching policies to a group
    job function.
    instead. Then, add the user to the appropriate group.
    Permissions policies (1/1187)
    G
    Create policy \[
    Choose one or more policies to attach to your new user.
    Filter by Type
    Q Search
    All types
    <1 2 34
    5
    6
    7
    60
    -
    Policy name \[
    Type
    V
    Attached entities
    O
    AccessAnalyzerServiceRolePolicy
    AWS managed
    O
    V
    AdministratorAccess
    AWS managed - job function
    0
    O
    AdministratorAccess-Amplify
    AWS managed
    O
    0
    AdministratorAccess-AWSElasticBeanstalk
    AWS managed
    O
    AlexaForBusinessDeviceSetup
    AWS managed
    O

[^24]: IAM > Users
    Users (1) Info
    C
    Delete
    Create user
    An IAM user is an identity with long-term credentials that is used to interact with AWS in an account.
    Q Search
    <
    1
    0
    User name
    Path
    Group:
    Last activity
    4
    MFA
    4
    Password age v Console last sign-in
    Access key
    chilops
    0

[^25]: Identity and Access
    X
    IAM > Users > chilops
    Management (IAM)
    chilops info
    Delete
    Q Search IAM
    Summary
    Dashboard
    ARN
    Console access
    Access key 1
    Access management
    arn:aws:iam: 158724841371:user/chilops
    Disabled
    Create access key
    User groups
    Created
    Last console sign-in
    Users
    April 23, 2024, 12:08 (UTC+05:30)
    Roles
    Policies
    Permissions
    Groups
    Tag
    Security credentials
    Access Advisor
    Identity providers
    Account settings
    Access reports
    Console sign-in
    Enable console access
    Access Analyzer
    External access
    Console sign-in link
    Console password
    https://158724841371.signin.aws.amazon.com/console
    Not enabled
    Unused access
    Analyzer settings
    Credential report
    Multi-factor authentication (MFA) (0)
    Remove
    Resync
    Assign MFA device
    Organization activity
    Use MFA to increase the security of your AWS environment. Signing in with MFA requires an authentication code from an MFA device. Each user can have a maximum of 8 MFA devices assigned. Learn more \[
    Service control policies
    Device type
    Identifier
    Certifications
    Created on
    Related consoles
    No MFA devices. Assign an MFA device to improve the security of your AWS environment
    IAM Identity Center \[Z
    Assign MFA device
    AWS Organizations \[
    Access keys (0)
    Create access key
    Use access keys to send programmatic calls to AWS from the AWS CLI, AWS Tools for PowerShell, AWS SDKs, or direct AWS API calls. You can have a maximum of two access keys (active or inactive) at a time. Learn more \[
    No access keys. As a best practice, avoid using long-term credentials like access keys. Instead, use tools which provide short term credentials. Learn more \[
    Create access key

[^26]: IAM > Users > chilops > Create access key
    Step 1
    Access key best practices &
    Access key best practices & alternatives Info
    alternatives
    Avoid using long-term credentials like access keys to improve your security. Consider the following use cases and alternatives.
    Step 2 - optional
    Use case
    Set description tag
    O Command Line Interface (CLI)
    You plan to use this access key to enable the AWS CLI to access your AWS account.
    Step 3
    Retrieve access keys
    O Local code
    You plan to use this access key to enable application code in a local development environment to access your AWS account.
    O Application running on an AWS compute service
    You plan to use this access key to enable application code running on an AWS compute service like Amazon EC2, Amazon ECS, or AWS Lambda to access
    your AWS account.
    O Third-party service
    You plan to use this access key to enable access for a third-party application or service that monitors or manages your AWS resources.
    O Application running outside AWS
    You plan to use this access key to authenticate workloads running in your data center or other infrastructure outside of AWS that needs to access your AWS
    resources.
    O Other
    Your use case is not listed here.
    A
    Alternatives recommended
    Use AWS CloudShell, a browser-based CLI, to run commands. Learn more
    . Use the AWS CLI V2 and enable authentication through a user in IAM Identity Center. Learn more \[
    Confirmation
    I understand the above recommendation and want to proceed to create an access key.
    Cancel
    Next

[^27]: Access key created
    This is the only time that the secret access key can be viewed or downloaded. You cannot recover it later. However, you can create a new access key any time.
    IAM > Users > chilops > Create access key
    Step 1
    Access key best practices &
    Retrieve access keys info
    alternatives
    Access key
    Step 2 - optional
    If you lose or forget your secret access key, you cannot retrieve it. Instead, create a new access key and make the old key inactive.
    Set description tag
    Access key
    Secret access key
    Step 3
    Retrieve access keys
    AKIASJ5F436N3DERUQGO
    Access key best practices
    . Never store your access key in plain text, in a code repository, or in code.
    . Disable or delete access key when no longer needed.
    . Enable least-privilege permissions.
    . Rotate access keys regularly.
    For more details about managing access keys, see the best practices for managing AWS access keys.
    Download .csv file
    Done

[^28]: \[ centos@ip-172-31-16-165 \~ \]$ aws configure
    AWS Access Key ID \[None \] : AKIASJ5F436N3DERUQGO
    AWS Secret Access Key \[None\] : yzZ9vj 5yOTCcY/isCrKlw+bXyoRaVODKArO/wgne
    Default region name \[None\] : us-east-1
    Default output format \[None\] :
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ \]

[^29]: \[ centos@ip-172-31-16-165 \~ \]$ aws configure
    AWS Access Key ID \[ \* \* \* \* \* \* \* \* \* \* \* \* \* \* \* \*UQGO\] :
    AWS Secret Access Key \[\* \* \* \* \* \* \* \* \*\* \*\*\* \*\*\*wgne\] :
    Default region name \[us-east-1\]:
    Default output format \[None\] :
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ \|

[^30]: 44 . 223.1.6 \| 172 . 31.16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ 1s -la
    total 24
    drwx-
    5 centos centos
    145 Apr 23 06:54
    drwxr-xr-x.
    3 root
    root
    20 Jan 16 13:13
    drwxrwxr-x
    2 centos centos
    39 Apr 23 06:45 . aws
    rw
    1 centos centos 2109 Apr 23 06:54 .bash history
    -rw-r--r-
    1 centos centos
    18 Apr
    2022 .bash_logout
    rw-r-
    -r
    1 centos centos
    141 Apr
    7 2022 .bash profile
    rw-r--r-
    1 centos centos
    376 Apr 7 2022 .bashrc
    -rw-r--r--.
    1 centos centos
    17 Jan 16 13:22 .gitconfig
    drwxrwxr-x
    3 centos centos 4096 Apr 23 05:14 shellscripts
    drwx-
    2 centos centos
    43 Jan 16 13:22 . ssh
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ cd . aws/
    44. 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~/. aws \]$ 1s
    config credentials
    44. 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~/. aws \]$ cat credentials
    \[default \]
    aws access key id = AKIASJ5F436N3DERUQGO
    aws secret_access_key = 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
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~/. aws \]$

[^31]: centosdip-172-31-16-165 \~/.aws \]$ aws ec2 run-instances --image-id ami-Of3c7d07486cad139 --instance-type t2.micro
    --secur
    ity-group-ids sg-0c9db47e9b4d484b6
    "Groups": \[\] ,
    " Instances" :
    "Ami LaunchIndex" : 0,
    "ImageId": "ami-Of3c7d07486cad139"
    "InstanceId": "i-04b66660881f833e0"
    "InstanceType": "t2.micro"
    "LaunchTime": "2024-04-23T06: 58 : 56+00:00",
    "Monitoring":

[^32]: Instances (1/2) Info
    C
    Connect
    Instance state
    Actions
    Launch instances
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    < 1 >
    Name _
    Instance ID
    Instance state
    4
    Instance type
    4
    Status check
    Alarm status
    Availability Zone
    Public IPV4 DNS
    4
    Public IPV4 ...
    4
    Elastic IP
    V
    i-04666660881f833ed
    Running
    Q Q
    t2.micro
    Initializing
    View alarms +
    us-east-1c
    ec2-52-5-138-134.com...
    52.5.138.134
    scripts
    i-06672f9cafdad5abf
    Running
    Q Q
    t2.micro
    2/2 checks passed View alarms +
    us-east-1d
    ec2-44-223-1-6.comput...
    44.223.1.6

[^33]: Users (1/1) Info
    An IAM user is an identity with long-term credentials that is used to interact with AWS in an account.
    Q Search
    V
    User name
    A
    Path
    V
    Group: V Last activity
    V
    MFA
    4
    Password age v Console last sign-in
    4
    Access ke
    chilops
    7 minutes ago
    Active - A
    Delete chilops?
    X
    Delete chilops permanently? This will also delete all its user data, security credentials
    and inline policies.
    User name
    Last activity
    chilops
    7 minutes ago
    Note: Recent activity usually appears within 4 hours. Data is stored for a maximum of 365 days,
    depending when your region began supporting this feature. Learn more
    This action cannot be undone.
    To confirm deletion, enter the user name in the text input field.
    chilops
    Cancel
    Delete user

[^34]: IAM > Roles > Create role
    Step 1
    Select trusted entity
    Select trusted entity info
    Step 2
    Trusted entity type
    Add permissions
    Step 3
    AWS service
    O AWS account
    O Web identity
    Name, review, and create
    w AWS services like EC2, Lambda, or others to perform actions
    Allow entities in other AWS accounts belonging to you or a 3rd
    Allows users federated by the specified external web identity
    in this account.
    party to perform actions in this account.
    provider to assume this role to perform actions in this account.
    O SAML 2.0 federation
    O Custom trust policy
    Allow users federated with SAML 2.0 from a corporate directory to
    Create a custom trust policy to enable others to perform actions in
    perform actions in this account.
    this account.
    Use case
    Allow an AWS service like EC2, Lambda, or others to perform actions in this account.
    Service or use case
    EC2
    Choose a use case for the specified service.
    Use case
    O EC2
    Allows EC2 instances to call AWS services on your behalf.
    O EC2 Role for AWS Systems Manager
    Allows EC2 instances to call AWS services like CloudWatch and Systems Manager on your behalf.
    O EC2 Spot Fleet Role
    Allows EC2 Spot Fleet to request and terminate Spot Instances on your behalf.
    O EC2 - Spot Fleet Auto Scaling
    Allows Auto Scaling to access and update EC2 spot fleets on your behalf.
    O EC2 - Spot Fleet Tagging
    Allows EC2 to launch spot instances and attach tags to the launched instances on your behalf.
    O EC2 - Spot Instances
    Allows EC2 Spot Instances to launch and manage spot instances on your behalf.
    O EC2 - Spot Fleet
    Allows EC2 Spot Fleet to launch and manage spot fleet instances on your behalf.
    O EC2 - Scheduled Instances
    Allows EC2 Scheduled Instances to manage instances on your behalf.
    Cancel
    Next

[^35]: IAM > Roles > Create role
    Step 1
    Add permissions info
    Select trusted entity
    Step 2
    Permissions policies (919) Info
    C
    Add permissions
    Choose one or more policies to attach to your new role.
    Filter by Type
    Step 3
    <
    Name, review, and create
    Q ec2fu
    X
    All types
    1 match
    Policy name \[
    4
    Type
    4
    Description
    + AmazonEC2FullAccess
    AWS managed
    Provides full access to Amazon EC2 via the...
    Set permissions boundary - optional
    Cancel
    Previous
    Next

[^36]: IAM > Roles > Create role
    Step 1
    Select trusted entity
    Add permissions info
    Step 2
    Permissions policies (2/919) Info
    C
    Add permissions
    Choose one or more policies to attach to your new role.
    Filter by Type
    Step 3
    Name, review, and create
    Q route53
    X
    All types
    V
    15 matches
    <
    Policy name \[
    A
    Type
    4
    Description
    0
    AmazonRoute53AutoNamingFullAccess
    AWS managed
    Provides full access to all Route 53 Auto N...
    AmazonRoute53AutoNamingReadOnlyAccess
    AWS managed
    Provides read-only access to all Route 53 ...
    0
    + AmazonRoute53AutoNamingRegistrantAccess
    AWS managed
    Provides registrant level access to Route 5...
    0
    AmazonRoute53DomainsFullAccess
    AWS managed
    Provides full access to all Route53 Domain...
    AmazonRoute53DomainsReadOnlyAccess
    AWS managed
    Provides access to Route53 Domains list a...
    + AmazonRoute53FullAccess
    AWS managed
    Provides full access to all Amazon Route 5...
    AmazonRoute53ReadOnlyAccess
    AWS managed
    Provides read only access to all Amazon R...
    AmazonRoute53RecoveryClusterFullAccess
    AWS managed
    Provides full access to Amazon Route 53 R...
    + AmazonRoute53RecoveryClusterReadOnlyAccess
    AWS managed
    Provides read only access to Amazon Rout...
    0
    AmazonRoute53RecoveryControlConfigFullAccess
    AWS managed
    Provides full access to Amazon Route 53 R...
    AmazonRoute53RecoveryControlConfigReadOnlyAccess
    AWS managed
    Provides read only access to Amazon Rout...
    0
    + AmazonRoute53RecoveryReadinessFullAccess
    AWS managed
    Provides full access to Amazon Route 53 R...
    AmazonRoute53RecoveryReadinessReadOnlyAccess
    AWS managed
    Provides read only access to Amazon Rout...
    0
    AmazonRoute53ResolverFullAccess
    AWS managed
    Full access policy for Route 53 Resolver
    AmazonRoute53ResolverReadOnlyAccess
    AWS managed
    Read only policy for Route 53 Resolver
    Set permissions boundary - optional
    Cancel
    Previous
    Next

[^37]: IAM > Roles > Create role
    Step 1
    Select trusted entity
    Name, review, and create
    Step 2
    Role details
    Add permissions
    Role name
    Step
    Enter a meaningful name to identify this role.
    Name, review, and create
    EC2Roleforshellscripts
    Maximum 64 characters. Use alphanumeric and '+=,.@-_' characters.
    Description
    Add a short explanation for this role.
    Allows EC2 instances to call AWS services on your behalf.
    Maximum 1000 characters. Use letters (A-Z and a-z), numbers (0-9), tabs, new lines, or any of the following characters: _+=,. @-/\\\[0\]!#$%^&\*();;"<>
    Step 1: Select trusted entities
    Edit
    Trust policy
    1 - {
    2
    "Version": "2012-10-17",
    3 +
    'Statement": \[
    4 .
    5
    "Effect": "Allow",
    "Action" : \[
    7
    "sts : AssumeRole"
    8
    9 .
    "Principal": {
    10 -
    "Service": \[
    11
    "ec2. amazonaws . com"
    12
    13
    14
    15
    16
    Step 2: Add permissions
    Edit
    Permissions policy summary
    Policy name \[
    Type
    A
    Attached as
    AmazonEC2FullAccess
    AWS managed
    Permissions policy
    AmazonRoute53FullAccess
    AWS managed
    Permissions policy
    Step 3: Add tags

[^38]: aws
    Services
    Q Search
    \[Alt+S\]
    4
    Global
    EC2
    Route 53
    BE IAM
    Identity and Access
    X
    Role EC2Roleforshellscripts created.
    View role
    Management (IAM)
    IAM > Roles
    Q Search IAM
    Roles (1/3) Info
    C
    Delete
    Create role
    An IAM role is an identity you can create that has specific permissions with credentials that are valid for short durations. Roles can be assumed by entities that you trust.
    Dashboard
    Q Search
    Access management
    Role name
    Trusted entities
    Last activity
    User groups
    Users
    AWSServiceRoleForSupport
    AWS Service: support (Service-Linked 53 days ago
    Roles
    AWSServiceRoleForTrustedAdvisor
    AWS Service: trustedadvisor (Service
    Policies
    V
    EC2Roleforshellscripts
    AWS Service: ec2
    Identity providers
    Account settings
    Roles Anywhere Info
    Manage
    Access reports
    Authenticate your non AWS workloads and securely provide access to AWS services.
    Access Analyzer
    External access
    Unused access
    Analyzer settings
    Access AWS from your non AWS workloads
    X.509 Standard
    Temporary credentials
    Credential report
    Operate your non AWS workloads using the same authentication and authorization
    Use your own existing PKI infrastructure or use AWS Certificate Manager Private
    Use temporary credentials with ease and benefit from the enhanced security they provide.
    Organization activity
    strategy that you use within AWS
    Certificate Authority \[ to authenticate identities.
    Service control policies

[^39]: Identity and Access
    X
    IAM > Roles > EC2Roleforshellscripts
    Management (IAM)
    EC2Roleforshellscripts Info
    Delete
    Q Search IAM
    Allows EC2 instances to call AWS services on your behalf.
    Summary
    Edit
    Dashboard
    Access management
    Creation date
    ARN
    Instance profile ARN
    April 23, 2024, 12:42 (UTC+05:30)
    arn:aws:iam: 158724841371:role/EC2Roleforshellscripts
    arn:aws:iam::158724841371:instance-profile/EC2Roleforshellscripts
    User groups
    Users
    Last activity
    Maximum session duration
    Roles
    1 hour
    Policies
    Identity providers
    Permissions
    Trust relationships
    Tags
    Access Advisor
    Revoke sessions
    Account settings
    Access reports
    Access Analyzer
    Permissions policies (2) Info
    C
    Simulate \[Z
    Remove
    Add permissions
    You can attach up to 10 managed policies.
    External access
    Unused access
    Filter by Type
    Analyzer settings
    Q Search
    All types
    Credential report
    Policy name \[
    Type
    Attached entities
    Organization activity
    Service control policies
    AmazonEC2FullAccess
    AWS managed
    AmazonRoute53FullAccess
    AWS managed
    Related consoles
    IAM Identity Center \[Z
    Permissions boundary (not set)
    AWS Organizations \[
    Generate policy based on CloudTrail events
    You can generate a new policy based on the access activity for this role, then customize, create, and attach it to this role. AWS uses your CloudTrail events to identify the services and actions used and generate a policy. Learn more
    Generate policy
    No requests to generate a policy in the past 7 days.

[^40]: Instances \| EC2 \| us-east-1
    < chilops
    x Delete or Archive old log files tl x (notes/session-17.txt at master x ( labautomation/tools/docker/ins x +
    X
    C
    https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,clien... @ A"
    W
    M
    . .
    aws
    Services
    Q Search
    \[Alt+S\]
    4
    N. Virginia
    chowdary
    EC2 Route 53
    BE IAN
    X
    EC2 Dashboard
    X
    Successfully terminated i-04b66660881f833e0
    EC2 Global View
    Instances (1/2) Info
    C Connect
    Instance state
    Actions
    Launch instances
    Events
    Connect
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    Console-to-Code Preview
    View details
    Name _
    Instance ID
    \|Instance state
    \| Instance type
    \| Status check
    \| Alarm status
    Availability Zone V \| Public IPV4 DNS
    Public IPV4 ... V EL
    Monit
    Manage instance state
    Instances
    -04b66660881f833ed
    Shutting-down
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    ec2-52-5-138-134.com..
    52.5.138.134
    disab
    Instance settings
    Instances
    scripts
    i-06672f9cafdad5abf
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1d
    ec2-44-223-1-6.comput...
    14.223.1.6
    disabl
    Networking
    Instance Types
    Launch Templates
    Change security groups
    Security
    Spot Requests
    Get Windows password
    Image and templates
    Monitor and troubleshoot
    Savings Plans
    Modify IAM role
    Reserved Instances
    Dedicated Hosts
    Capacity Reservations New
    Images
    AMIs
    AMI Catalog
    Elastic Block Store
    Volumes
    O X
    Snapshots
    i-06672f9cafdad5abf (scripts)
    Lifecycle Manager
    Details
    Status and alarms New
    Monitoring
    Security
    Networking
    Storage
    Tags
    Network & Security
    Security Groups
    Instance summary Info
    Elastic IPs
    Instance ID
    Public IPV4 address
    Private IPv4 addresses
    Placement Groups
    i-06672f9cafdad5abf (scripts)
    44.223.1.6 \| open address \[
    172.31.16.165
    Key Pairs
    IPv6 address
    Instance state
    Public IPV4 DNS
    Network Interfaces
    Running
    ec2-44-223-1-6.compute-1.amazonaws.com \| open address \[
    Load Balancing
    Load Balancers
    Hostname type
    Private IP DNS name (IPv4 only)
    IP name: ip-172-31-16-165.ec2.internal
    Target Groups
    ip-172-31-16-165.ec2.internal
    Trust Stores New
    Answer private resource DNS name
    Instance type
    Elastic IP addresses
    Auto Scaling
    IPV4 (A)
    t2.micro
    Auto Scaling Groups
    Auto-assigned IP address
    /PC ID
    AWS Compute Optimizer finding
    Opt-in to AWS Compute Optimizer for recommendations. \| Learn more \[
    44.223.1.6 \[Public IP\]
    vpc-0817cae8968304c06 \[
    IAM Role
    Subnet ID
    Auto Scaling Group name
    subnet-076650bcf0b486323 \[
    MDSv2
    CloudShell
    Feedback
    @2024, Amazon Web Services, Inc. or its affiliates.
    Privacy Terms Cookie preferences
    1 NASDAQ
    12:46
    +1.11%
    23-04-2024

[^41]: =
    EC2 > Instances > i-06672f9cafdad5abf > Modify IAM role
    Modify IAM role info
    Attach an IAM role to your instance.
    Instance ID
    i-06672f9cafdad5abf (scripts)
    IAM role
    Select an IAM role to attach to your instance or create a new role if you haven't created any. The role you select replaces any roles that are
    currently attached to your instance.
    EC2Roleforshellscripts
    C
    Create new IAM role \[
    Cancel
    Update IAM role

[^42]: EC2
    ECZ
    ECZ

[^43]: \[ centosdip-172-31-16-165 \~ \]$ rm -rf . aws/config
    44 . 223.1.6 \| 172. 31.16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$ rm -rf .aws/cred
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centos@ip-172-31-16-165 \~ \]$
    44 . 223.1.6 \| 172. 31.16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 \~ \]$ aws ec2 run-instances --image-id ami-Of3c7d07486cad139 --instance-type t2.micro --security-
    roup-ids sg-0c9db47e9b4d484b6
    An error occurred (AuthFailure) when calling the RunInstances operation: AWS was not able to validate the provided access
    redentials
    44 . 223.1.6 \| 172. 31. 16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 \~ \]$ rm -rf .aws/credentials
    44. 223.1.6 \| 172. 31.16.165 \| t2.micro \| null
    \[ centosdip-172-31-16-165 \~ \]$ aws ec2 run-instances --image-id ami-Of3c7d07486cad139 --instance-type t2.micro --security-
    roup-ids sg-0c9db47e9b4d484b6
    "Groups": \[\] ,
    "Instances": \[
    "Ami LaunchIndex" : 0,
    "ImageId": "ami-Of3c7d07486cad139"
    "InstanceId": "i-018dc753b969393d3"
    "InstanceType": "t2.micro"
    "LaunchTime": "2024-04-23T07 : 21 : 59+00:00",
    "Monitoring":

[^44]: Successfully attached EC2Roleforshellscripts to instance i-06672f9cafdad5abf
    Instances (1/3) Info
    C
    Connect
    Instance state
    Actions
    Launch instances
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    1 >
    Name _
    4
    Instance ID
    Instance state
    Instance type
    4
    Status check
    Alarm status
    Availability Zone
    Public IPV4 DNS
    4
    Public IPv4 ...
    Elastic IP
    IPV6 IPS
    V
    i-018dc7536969393d3
    Running
    Q Q
    2.micro
    Initializing
    View alarms +
    us-east-1d
    ec2-54-86-141-238.co...
    54.86.141.238
    O
    i-04b66660881f833e0
    Terminated
    Q Q
    t2.micro
    View alarms +
    us-east-1c
    scripts
    i-06672f9cafdad5abf
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1d
    ec2-44-223-1-6.comput...
    44.223.1.6

[^45]: Robosho-shellscripts > $ roboshop.sh
    #! /bin/bash
    AMI=ami -Of3c7d07486cad139 #this keeps on changing
    UI A W N
    SG_ID=sg-0c9db47e9b4d484b6 #replace with your SG ID
    INSTANCES=("mongodb" "redis" "mysql" "rabbitmq" "catalogue" "user" "cart" "shipping" "payment" "dispatch" "web")
    ZONE_ID=Z06431971951XUVZELNIC # replace your zone ID
    DOMAIN_NAME="chowdarychilukuri . in"
    9
    for i in "$ {INSTANCES\[@\]\]"
    10
    do
    11
    if \[ $i == "mongodb" \] \| \| \[ $i == "mysql" \] \|\| \[ $i == "shipping" \]
    12
    then
    13
    INSTANCE_TYPE="t3. small"
    14
    else
    15
    INSTANCE_TYPE="t2.micro"
    16
    fi
    17
    18
    IP_ADDRESS=$ (aws ec2 run-instances --image-id $AMI - - instance-type $INSTANCE_TYPE --security-group-ids $SG_ID --tag-specifications
    19
    echo "$1: $IP_ADDRESS"
    20
    21
    #create R53 record, make sure you delete existing record
    22
    aws route53 change-resource-record-sets \\
    23
    --hosted-zone-id $ZONE_ID \\
    24
    - -change-batch
    25
    26
    "Comment": "Creating a record set for cognito endpoint"
    27
    "Changes" : \[{
    28
    "Action"
    "UPSERT"
    29
    "ResourceRecordSet"
    :
    30
    "Name"
    "$1 '. '$DOMAIN_NAME " "
    31
    "Type"
    32
    " TTL "
    33
    , "ResourceRecords"
    34
    "Value"
    "$IP ADDRESS ' "
    35
    36
    37
    38
    39
    40
    done

[^46]: -tag-specifications "ResourceType=instance, Tags=\[{Key=Name, Value=$i} \]" --query 'Instances\[0\]. PrivateIpAddress' --output text)

[^47]: PROBLEMS
    OUTPUT
    DEBUG CONSOLE
    TERMINAL
    PORTS
    On branch main
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
    roboshop . sh
    nothing added to commit but untracked files present (use "git add" to track)
    PS E: \\AWSDevops\\Repos \\Robosho-shellscripts> git add . ; git commit -m "instances & hosted zones creation; git push origin main

[^48]: \[ centosdip-172-31-19-185 \~ \]$ git clone https: //github. com/chilops/Roboshop-shellscripts.git
    Cloning into 'Roboshop-shellscripts' .. .
    remote: Enumeratiog objects: 68, done.
    remote: Counting objects: 100% (68/68), done.
    remote: Compressing objects: 100% (52/52), done.
    remote: Total 68 (delta 37), reused 46 (delta 15), pack-reused 0
    Receiving objects: 100% (68/68), 9.95 KiB \| 3.32 MiB/s, done.
    Resolving deltas: 100% (37/37), done.
    54 . 227.20.6 \| 172. 31. 19.185 \| t2.micro \| null
    \[ centosdip-172-31-19-185 \~ \]$ 1s
    Roboshop-shellscripts
    54. 227.20.6 \| 172. 31. 19. 185 \| t2.micro \| null
    \[ centos@ip-172-31-19-185 \~ \]$ cd Roboshop-shellscripts/
    54. 227.20.6 \| 172. 31. 19.185 \| t2.micro \| https: / /github. com/chilops/Roboshop-shellscripts. git
    \[ centosdip-172-31-19-185 \~/Roboshop-shellscripts \]$ 1s
    cart . service
    catalogue . sh mysql . repo
    payment . sh
    roboshop . conf
    user . service
    cart . sh
    Mongodb . sh
    mysql . sh
    rabbitmq . sh
    shipping . service
    user . sh
    catalogue . service
    mongo . repo
    payment . service
    redis. sh
    shipping . sh
    web . sh
    54.227.20.6 \| 172. 31. 19.185 \| t2.micro \| https: / /github. com/chilops/Roboshop-shellscripts.git
    \[ centosdip-172-31-19-185 \~/Roboshop-shellscripts \]$ \[

[^49]: \[ centosdip-172-31-19-185 \~/Roboshop-shellscripts \]$ sh roboshop. sh
    mongodb: 172 . 31 . 24. 151
    "ChangeInfo" : {
    "Id": "/change/C066055337SF7QVOHZG3R",
    "Status": "PENDING"
    "SubmittedAt": "2024-04-24T05 : 09 : 43. 749000+00:00",
    "Comment": "Creating a record set for cognito endpoint"
    redis: 172. 31 . 82.240
    "ChangeInfo" : {
    "Id": "/change/C0694249JXSB35F76VE9"
    "Status": "PENDING"
    "SubmittedAt": "2024-04-24T05 : 09 : 46. 839000+00:00",
    "Comment": "Creating a record set for cognito endpoint"
    mysql: 172 . 31 . 21 . 102
    "ChangeInfo" : {
    "Id": "/change/C03953923F8KEOOOKEI 3G"
    "Status": "PENDING",
    "SubmittedAt": "2024-04-24T05 : 09 : 50 . 335000+00:00",
    "Comment": "Creating a record set for cognito endpoint"
    rabbitmq: 172 . 31 . 91. 170
    "ChangeInfo" :

[^50]: Instances (11/12) Info
    C
    Connect
    Instance state
    Actions
    4
    Launch instances
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    < 1 >
    -
    Name _
    4
    Instance ID
    Instance state
    4
    Instance type
    Status check
    Alarm status
    Availability
    V
    shipping
    i-Of4be341034fe544f
    Running
    t3.small
    Initializing
    View alarms +
    us-east-1d
    script
    i-002f1da6881cfefac
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1d
    V
    mongodb
    i-0044c8becae3fod3e
    Running
    t3.small
    2/2 checks passed View alarms +
    us-east-1d
    V
    redis
    i-01418dd640ca8f43a
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    V
    rabbitmq
    i-0827a1c8a4c2154cd
    Running
    Q Q
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    V
    user
    i-09773d2aa4fgeb 12c
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    V
    mysql
    i-0c8769739f1a46576
    Running
    t3.small
    2/2 checks passed View alarms +
    us-east-1d
    catalogue
    i-07962340a090a8d50
    Running
    t2.micro
    Initializing
    View alarms +
    us-east-1c
    dispatch
    i-0ea598ed574ce77bd
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    V
    payment
    i-0c21dac14deb3da7a
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    V
    cart
    i-0992a4b41aefc7674
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c
    V
    web
    i-02cbf70d809142012
    Running
    t2.micro
    2/2 checks passed View alarms +
    us-east-1c

[^51]: Records (13) Info
    Delete record
    Import zone file
    Create record
    Automatic mode is the current search behavior optimized for best filter results. To change modes go to settings.
    Q Filter records by property or value
    Type
    Routing policy
    Alias
    <
    1
    O
    Record name
    4
    Type
    Routin...
    4
    Differ...
    4
    Alias
    4
    Value/Route traffic to
    TTL
    chowdarychilukuri.in
    A
    Simple
    No
    54.210.40.88
    1
    ns-59.awsdns-07.com.
    ns-1889.awsdns-44.co.uk.
    0
    chowdarychilukuri.in
    NS
    Simple
    No
    172
    ns-1039.awsdns-01.org.
    ns-836.awsdns-40.net.
    O
    chowdarychilukuri.in
    SOA
    Simple
    No
    ns-59.awsdns-07.com. awsdn...
    900
    0
    cart.chowdarychilukuri.in
    A
    Simple
    No
    172.31.84.212
    1
    0
    catalogue.chowdarychilukuri.in
    4
    Simple
    No
    172.31.89.156
    0
    dispatch.chowdarychilukuri.in
    A
    Simple
    No
    172.31.87.188
    0
    mongodb.chowdarychilukuri.in
    A
    Simple
    No
    172.31.24.151
    0
    mysql.chowdarychilukuri.in
    A
    Simple
    No
    172.31.21.102
    0
    payment.chowdarychilukuri.in
    A
    Simple
    No
    172.31.89.25
    0
    rabbitmq.chowdarychilukuri.in
    A
    Simple
    No
    172.31.91.170
    0
    redis.chowdarychilukuri.in
    A
    Simple
    No
    172.31.82.240
    0
    shipping.chowdarychilukuri.in
    A
    Simple
    No
    172.31.20.58
    user.chowdarychilukuri.in
    A
    Simple
    No
    172.31.87.121

