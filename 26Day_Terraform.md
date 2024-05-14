---
title: 26Day_Terraform
uuid: 3d5f36c2-11b8-11ef-af96-9a665e06d35f
version: 373
created: '2024-05-14T11:37:27+05:30'
tags:
  - terraform
---

\

***Topics:***

1. *<mark style="background-color:#f8d616;">Variables & datatypes in Terraform<!-- {"backgroundCycleColor":"25"} --></mark>*

    1. *If variable not declared*

    1. *variables overriding*

\

\

*<mark style="background-color:#f8914d;">Variables & datatype in Terraform:<!-- {"backgroundCycleColor":"24"} --></mark>*

\

*Created Variables folder and added provider.tf code.*

![f749ec72-b37b-4277-8ebd-18f7d135694b.png|991.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/f749ec72-b37b-4277-8ebd-18f7d135694b.png) [^1]

\

```
cd terraform/
cd variables/
terraform init
```

![a9a5be29-6b68-49a3-b57f-d3a047d2e48a.png|660](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/a9a5be29-6b68-49a3-b57f-d3a047d2e48a.png) [^2]

\

*Created Ec2.tf & variables.tf files.  -- In Ec2.tf variables given "**var.ami_id**" but not declared in variables.tf file so error will get as below*

![ab09ec45-a29a-4322-af6c-3cef1f9af8c4.png|928.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/ab09ec45-a29a-4322-af6c-3cef1f9af8c4.png) [^3]

\

```
terraform plan
```

![810da410-0437-477e-8179-85ee9f3621de.png|884.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/810da410-0437-477e-8179-85ee9f3621de.png) [^4]

\

*EC2.tf code for only instance launch*

![b8f2fd95-51e5-451e-b977-5f06ae656442.png|816](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/b8f2fd95-51e5-451e-b977-5f06ae656442.png) [^5]

\

*its variable.tf code*

![d64d742a-e7c4-4eb8-8db9-2ff4a1e336d4.png|559](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/d64d742a-e7c4-4eb8-8db9-2ff4a1e336d4.png) [^6]

\

```
terraform plan
```

```
terraform apply -auto-approve
```

![5a0eb37b-a9fa-432c-bbc3-31855f766a42.png|700](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/5a0eb37b-a9fa-432c-bbc3-31855f766a42.png) [^7]

\

![c4bdd5c4-3e7f-4b63-b7a6-30f8df90109d.png|788.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/c4bdd5c4-3e7f-4b63-b7a6-30f8df90109d.png) [^8]

```
terraform destroy -auto-approve
```

![6674e7de-2ada-4530-a2fe-1c05fa47c7e1.png|815.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/6674e7de-2ada-4530-a2fe-1c05fa47c7e1.png) [^9]

![e845c21f-a62f-41e9-b2ba-819208d702f2.png|813](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/e845c21f-a62f-41e9-b2ba-819208d702f2.png) [^10]

\

![f1bf2877-5144-46ac-b6d1-aacb748c43ef.png|828](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/f1bf2877-5144-46ac-b6d1-aacb748c43ef.png) [^11]

\

\

*Now create separate sg.tf file for security group:*

![b9ec75b6-9f60-4801-8204-55f6c5925615.png|806](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/b9ec75b6-9f60-4801-8204-55f6c5925615.png) [^12]

\

*ec2.tf code*

![7adca136-34d6-4198-96b0-0d01e2c7dfd3.png|803](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/7adca136-34d6-4198-96b0-0d01e2c7dfd3.png) [^13]

\

*variables.tf file for ec2 & security group:*

![f4661e73-15ae-4bf1-bff6-d5642ad16243.png|697](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/f4661e73-15ae-4bf1-bff6-d5642ad16243.png) [^14]

\

```
terraform plan
```

```
terraform apply -auto-approve
```

\

![5bb3df6f-efbf-4993-a432-eafe85d90f99.png|820.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/5bb3df6f-efbf-4993-a432-eafe85d90f99.png) [^15]

![f03a5683-d598-4523-82de-58f367fadb30.png|821](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/f03a5683-d598-4523-82de-58f367fadb30.png) [^16]

\

![178021e2-ad28-4abb-b8b5-3d5f6348772c.png|847.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/178021e2-ad28-4abb-b8b5-3d5f6348772c.png) [^17]

\

*Instance tags*

![486d900c-f6a4-456e-a9c9-0a69b15a673f.png|864](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/486d900c-f6a4-456e-a9c9-0a69b15a673f.png) [^18]

*Also security group created*

![2972b8e7-ef2d-4708-bcc9-2d36e3aa90e9.png|905.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/2972b8e7-ef2d-4708-bcc9-2d36e3aa90e9.png) [^19]

\

```
terraform destroy -auto-approve
```

![f463e5ad-f400-4d82-99f6-5706310483fc.png|729](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/f463e5ad-f400-4d82-99f6-5706310483fc.png) [^20]

\

1. *<mark style="background-color:#f8914d;">**If variable not declared**<!-- {"backgroundCycleColor":"24"} --></mark>*<!-- {"indent":1} -->

*Commented as below*

![952aa842-0cd0-46ba-83c6-cd499fe3c72c.png|716](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/952aa842-0cd0-46ba-83c6-cd499fe3c72c.png) [^21]

\

*Now its asking for AMI-ID value*

```
terraform plan
```

![](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/5a9d7301-5aaf-4fcb-9401-168a2ad0aa7d.png) [^22]

\

*<mark style="background-color:#f8914d;">**variables overriding**<!-- {"backgroundCycleColor":"24"} --></mark>*

*<mark>**terraform.tfvars is used to overwrite the default values in variable.tf file.**</mark>*

*.<mark>tfvars extension can create any other files like roboshop.tfvars</mark>*

*Create **terraform.tfvars** file - values we can give in this file like 't3.small' etc.*

![f267ece5-4880-4ebb-aa23-62a859c88f6e.png|576](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/f267ece5-4880-4ebb-aa23-62a859c88f6e.png) [^23]

\

*But in **variables.tf** file instance type is **t2.micro** now **terraform.tfvars** will override & creates <mark style="background-color:#f3de6c;">**t3.small**<!-- {"backgroundCycleColor":"14"} --></mark> instance.*

![](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/03e12952-8c45-4bc3-81c2-da74c6da2761.png) [^24]

\

*Uncommented which previously commented*

![0e7703b5-e487-4e19-b104-7eac4a7c40dc.png|666](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/0e7703b5-e487-4e19-b104-7eac4a7c40dc.png) [^25]

\

*Now you can see t3.small instance*

```
terraform plan
```

![745f818b-8fd1-40b4-a3c4-ca86489df7f2.png|708](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/745f818b-8fd1-40b4-a3c4-ca86489df7f2.png) [^26]

\

*Or we can declare variables when we are executing terraform plan*

```
terraform plan -var="instance_type=t3.medium"
```

![3b45d2bd-ca64-4df5-91ff-46d89a7fa133.png|890.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/3b45d2bd-ca64-4df5-91ff-46d89a7fa133.png) [^27]

\

\

*Creating some file with .tfvars... Ex: roboshop.tfvars*

![6fce9d1c-b6e0-4971-ac6d-083ce89116a3.png|611](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/6fce9d1c-b6e0-4971-ac6d-083ce89116a3.png) [^28]

\

```
terraform plan -var-file="roboshop.tfvars"
```

![3bf07e06-0b29-4d0b-88b5-d34e7032ff55.png|946.3333740234375](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/3bf07e06-0b29-4d0b-88b5-d34e7032ff55.png) [^29]

\

*using environmental variables:*

![b8d6c63c-95f8-4e9a-a7e0-ab8752f2b6eb.png|724](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/b8d6c63c-95f8-4e9a-a7e0-ab8752f2b6eb.png) [^30]

![](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/6a4db553-3b6e-47af-b618-941b0a500cc3.png)

\

```
terraform plan -var-file="roboshop.tfvars" -var="instance_type=t3.medium"
```

![](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/486fdad9-f52f-4c30-99d4-6c00491eaeed.png) [^31]

![df77d49e-b44d-4c6f-ac45-86fee22c9995.png|393](https://images.amplenote.com/3d5f36c2-11b8-11ef-af96-9a665e06d35f/df77d49e-b44d-4c6f-ac45-86fee22c9995.png) [^32]

\

*29.15*

\

\

[^1]: V REPOS
    terraform > variables > provider.tf > ...
    > Ansible
    1
    terraform {
    > Concepts
    2
    required_providers {
    > notes
    aws = {
    4
    source = "hashicorp/aws"
    > Robosho-shellscripts
    M
    5
    version = "5.49.0" #AWS provider version, not terraform version
    > roboshop-ansible
    6
    > roboshop-ansible-roles
    7
    > shellscripts
    18
    terraform
    9
    > session1 \\ EC2
    10
    provider "aws" {
    11
    region = "us-east-1"
    variables
    12
    provider.tf -
    13
    .gitignore
    i README.MD
    U

[^2]: MINGW64:/e/awsdevops/Repos/terraform/variables
    chowd@Chowdary MINGW64 /
    $ cd /e/awsdevops /Repos/
    chowd@Chowdary MINGW64 /e/awsdevops /Repos (main)
    $ cd terraform/
    chowd@chowdary MINGW64 /e/awsdevops/Repos/terraform (main)
    $ cd variables/
    chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform/variables (main)
    s terraform init
    Initializing the backend. ..
    Initializing provider plugins ...
    Terraform has been successfully initialized!
    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. All Terraform commands
    should now work.
    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    chowd@Chowdary MINGW64 /e/awsdevops /Repos/terraform/variables (main)

[^3]: REPOS
    terraform > variables > ec2.tf > % resource "aws_instance" "web"
    > Ansible
    1
    resource "aws_instance" "web" {
    > Concepts
    2
    ami
    = var . ami_id #devops-practice
    3
    > notes
    instance_type = "t2.micro"
    14
    Robosho-shellscripts
    #vpc_security_group_ids = \[aws_security_group . roboshop-all. id\] #This means list
    M
    5
    > roboshop-ansible
    6
    tags = {
    > roboshop-ansible-roles
    17
    Name = "HelloTerraform"
    > shellscripts
    8
    v terraform
    9
    v session 1 \\ EC2
    > .terraform
    E .terraform.lock.hcl
    ec2.tf
    provider.tf
    {} terraform.tfstate
    E terraform.tfstate.backup
    variables.tf
    variables
    > .terraform
    E .terraform.lock.hcl
    U
    ec2.tf
    1, U
    provider.tf
    U
    variables.tf
    U

[^4]: PS E: \\AWSDevops \\Repos \\terraform\\variables> terraform plan
    Error: Reference to undeclared input variable
    on ec2.tf line 2, in resource "aws_instance" "web":
    2:
    ami
    = var . ami_id #devops-practice
    An input variable with the name "ami_id" has not been declared. This variable can be declared with a variable "ami_id" {} block.
    PS E: \\AWSDevops \\Repos \\terraform\\variables>

[^5]: terraform > variables > ec2.tf > { resource "aws_instance" "web"
    resource "aws_instance" "web" {
    2
    ami
    = var . ami_id #devops-practice
    3
    instance_type = var . instance_type
    4
    #vpc_security_group_ids = \[aws_security_group . roboshop-all. id\]
    #This means list
    tags = var . tags

[^6]: terraform > variables > variables.tf > < variable "tags"
    1
    # 1. command line
    2
    # 2. -var-file
    3
    # 3. terraform . tfvars
    4
    # 4. ENV variables
    5
    6
    variable "ami_id" {
    7
    type = string
    8
    default = "ami-Of3c7d07486cad139"
    9
    10
    11
    variable "instance_type" {
    12
    default = "t2.micro"
    13
    type = string
    14
    15
    16
    variable "tags" {
    17
    type = map
    #map variable types
    18
    default = {
    19
    Name = "Hello Terraform"
    20
    Project = "Roboshop"
    21
    Environment = "DEV"
    22
    Component = "Web"
    23
    Terraform = "true"
    24
    25

[^7]: Plan: 1 to add, 0 to change, 0 to destroy.
    aws_instance. web: Creating. . .
    aws_instance.web: Still creating... \[10s elapsed\]
    aws_instance.web: Still creating... \[20s elapsed\]
    aws instance. web: Still creating... \[30s elapsed\]
    aws_instance. web: Creation complete after 36s \[id=i-03066e96a45fbe442\]
    Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
    PS E: \\AWSDevOps\\Repos \\terraform\\variables>

[^8]: Instances (1) Info
    G
    Connect
    Instance state
    Actions
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    Name _
    4
    Instance ID
    Instance state
    4
    Instance type
    4
    Status check
    Hello Terraform
    i-03066e96a45fbe442
    Pending
    t2.micro

[^9]: PS E: \\AWSDevops \\Repos \\terraform\\variables> terraform destroy -auto-approve
    aws_instance.web: Refreshing state. .. \[id=i-03066e96a45fbe442\]
    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    - destroy
    Terraform will perform the following actions:
    # aws_instance.web will be destroyed
    resource "aws_instance" "web" {
    ami
    = "ami-Of3c7d07486cad139" -> null
    1 : 158724841371:
    93066-96245fbe447 "

[^10]: Plan: 0 to add, 0 to change, 1 to destroy.
    aws_instance . web: Destroying... \[id=i-03066e96a45fbe442\]
    aws_instance.web: Still destroying... \[id=i-03066e96a45fbe442, 10s elapsed\]
    aws_instance.web: Still destroying... \[id=i-03066e96a45fbe442, 20s elapsed\]
    aws_instance.web: Still destroying... \[id=i-03066e96a45fbe442, 30s elapsed\]
    aws instance. web: Destruction complete after 33s
    Destroy complete! Resources: 1 destroyed.
    PS F: \\AWSDevOps \\Repos\\terraform\\variables> l

[^11]: Instances (1) Info
    C
    Connect
    Instance state
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    Name _
    V
    Instance ID
    Instance state
    V
    Instance type
    A
    Hello Terraform
    i-03066e96a45fbe442
    Terminated
    t2.micro

[^12]: terraform > variables > sg.tf > % resource "aws_security_group" "roboshop-all" > { egress > . protocol
    1
    resource "aws_security_group" "roboshop-all" { #This is terraform name, for terraform reference only
    2
    name
    = var . sg-name #This is AWS name which reflects in AWS
    3
    description = var . sg-description
    4
    #vpc_id
    = aws_vpc . main. id
    15
    6
    ingress {
    7
    description
    = "Allow All ports"
    8
    from_port
    = var . inbound-from-port #0 means all ports
    9
    to_port
    = 0
    10
    protocol
    "tcp"
    11
    cidr_blocks
    = var . cidr_blocks
    12
    #ipv6_cidr_blocks = \[aws_vpc . main . ipv6_cidr_block\]
    13
    14
    15
    egress {
    16
    from_port
    e
    17
    to_port
    18
    protocol
    11-1"
    19
    cidr_blocks
    = \["0.0.0.0/0"\]
    20
    #ipv6_cidr_blocks = \[": :/0"\]
    21
    22
    23
    tags = {
    24
    Name = "roboshop-all-aws"
    25
    26

[^13]: terraform > variables > ec2.tf > % resource "aws_instance" "web" > \[ \] vpc_security_group_ids
    1
    resource "aws_instance" "web" {
    2
    ami
    = var . ami_id #devops-practice
    instance_type = var . instance_type
    14
    vpc_security_group_ids = \[aws_security_group . roboshop-all. id\] #This means list
    15
    6
    tags = var . tags
    7

[^14]: terraform > variables > variables.tf > $ variable "sg-name" > @ type
    4
    # 4. ENV variables
    5
    6
    variable "ami_id" {
    7
    type = string
    8
    default = "ami-Of3c7d07486cad139"
    9
    10
    11
    variable "instance_type" {
    12
    default = "t2.micro"
    13
    type = string
    14
    15
    16
    variable "tags" {
    17
    type = map
    #map variable types
    18
    default = {
    19
    Name = "Hello Terraform"
    20
    Project = "Roboshop"
    21
    Environment = "DEV"
    22
    Component = "Web"
    23
    Terraform = "true"
    24
    25
    26
    27
    variable "sg-name" {
    28
    type = string
    29
    default = "roboshop-all"
    30
    31
    32
    variable "sg-description" {
    33
    type = string
    34
    default = "allowing all ports"
    35
    36
    37
    variable "inbound-from-port" {
    38
    type = number
    39
    default = 0
    40
    41
    42
    variable "cidr_blocks" {
    43
    type = list
    44
    default = \["0.0.0.0/0"\]
    45

[^15]: PS E: \\AWSDevops \\Repos \\terraform\\variables> terraform apply -auto-approve
    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    + create
    Terraform will perform the following actions:
    # aws_instance. web will be created
    + resource "aws_instance" "web" {
    ami
    = "ami -Of3c7d07486cad139"
    arn
    = (known after apply)

[^16]: Plan: 2 to add, 0 to change, 0 to destroy.
    aws_security_group . roboshop-all: Creating...
    aws_security_group. roboshop-all: Creation complete after 6s \[id=sg-04ba5dccf6fe618ff\]
    aws_instance. web: Creating. . .
    aws_instance.web: Still creating... \[10s elapsed\]
    aws_instance.web: Still creating. ..
    \[20s elapsed\]
    aws_instance.web: Still creating... \[30s elapsed\]
    aws_instance. web: Creation complete after 36s \[id=i-0d40508c555cd0a28\]
    Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
    PS E: \\AWSDevops \\Repos \\terraform\\variables>

[^17]: Instances (2) Info
    C
    Connect
    Instance state
    Actions
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    Name _
    Instance ID
    Instance state
    4
    Instance type
    4
    Status check
    Hello Terraform
    i-03066e96a45fbe442
    Terminated
    t2.micro
    Hello Terraform
    i-Od40508c555cd0a28
    Running
    t2.micro
    Initializing

[^18]: i-0d40508c555cd0a28 (Hello Terraform)
    Details
    Status and alarms New
    Monitoring
    Security
    Networking
    Storage
    Tags
    Tags
    Q
    Key
    Value
    Component
    Web
    Environment
    DEV
    Terraform
    true
    Project
    Roboshop
    Name
    Hello Terraform

[^19]: i-0d40508c555cd0a28 (Hello Terraform)
    Details
    Status and alarms New
    Monitoring
    Security
    Networking
    Storage
    Tags
    Security details
    IAM Role
    Owner ID
    Launch time
    158724841371
    Tue May 14 2024 12:29:25
    Security groups
    \[ sg-04ba5dccf6fe618ff (roboshop-all)

[^20]: Plan: 0 to add, 0 to change, 2 to destroy.
    aws_instance. web: Destroying. .. \[id=i-0d40508c555cd0a28\]
    aws_instance.web: Still destroying. .. \[id=i-0d40508c555cd0a28, 10s elapsed\]
    aws_instance.web: Still destroying. .. \[id=i-0d40508c555cd0a28, 20s elapsed\]

[^21]: terraform > variables > variables.tf > % variable "ami_id"
    1
    # 1. command line
    # 2. -var-file
    3
    # 3. terraform. tfvars
    4
    # 4. ENV variables
    5
    16
    variable "ami_id" {
    7
    type = string
    8
    #default = "ami-Of3c7d07486cad139"

[^22]: PS E: \\AWSDevops \\Repos \\terraform\\variables> terraform plan
    var . ami id
    Enter a value:

[^23]: terraform > variables > terraform.tfvars > . instance_type
    1
    instance_type = "t3. small"

[^24]: terraform > variables > variables.tf > % variable "instance_type" > . default
    1
    # 1. command line
    # 2. -var-file
    3
    # 3. terraform. tfvars
    4
    # 4. ENV variables
    5
    6
    variable "ami_id" {
    7
    type = string
    8
    #default = "ami-Of3c7d07486cad139"
    9
    10
    11
    variable "instance_type" {
    12
    default = "t2.micro"
    13
    type = string
    14
    15

[^25]: terraform > variables > variables.tf > % variable "ami_id" > ) default
    1
    # 1. command line
    12
    # 2. -var-file
    13
    # 3. terraform. tfvars
    4
    # 4. ENV variables
    5
    6
    variable "ami_id" {
    7
    type = string
    8
    default = "ami-Of3c7d07486cad139" _
    9

[^26]: Terraform will perform the following actions:
    # aws_instance.web will be created
    + resource "aws_instance" "web" {
    + ami
    = "ami-Of3c7d07486cad139"
    + arn
    = (known after apply)
    +
    associate_public_ip_address
    = (known after apply)
    +
    availability_zone
    = (known after apply)
    +
    cpu_core_count
    = (known after apply)
    +
    cpu_threads_per_core
    = (known after apply)
    +
    disable_api_stop
    = (known after apply)
    +
    disable_api_termination
    = (known after apply)
    + ebs_optimized
    = (known after apply)
    +
    get_password_data
    = false
    +
    host id
    = (known after apply)
    +
    host_resource_group_arn
    = (known after apply)
    + iam_instance_profile
    = (known after apply)
    +
    id
    = (known after apply)
    +
    instance_initiated_shutdown_behavior = (known after apply)
    + instance_lifecycle
    = (known after apply)
    + instance_state
    = (known after apply)
    + instance_type
    = "t3. small"
    +
    ipv6_address_count
    = (known after apply)

[^27]: PS E: \\AWSDevops \\Repos \\terraform\\variables> terraform plan -var="instance_type=t3.medium"
    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    + create
    Terraform will perform the following actions:
    # aws_instance.web will be created
    resource "aws_instance" "web" {
    + ami
    = "ami-Of3c7d07486cad139"
    + arn
    = (known after apply)
    + associate_public_ip_address
    = (known after apply)
    + availability_zone
    = (known after apply)
    cpu_core_count
    = (known after apply)
    +
    cpu_threads_per_core
    = (known after apply)
    disable_api_stop
    = (known after apply)
    + disable_api_termination
    = (known after apply)
    ebs_optimized
    = (known after apply)
    get_password_data
    = false
    + host id
    = (known after apply)
    + host_resource_group_arn
    = (known after apply)
    + iam_instance_profile
    = (known after apply)
    + id
    = (known after apply)
    instance_initiated_shutdown_behavior = (known after apply)
    + instance_lifecycle
    = (known after apply)
    + instance_state
    = (known after apply)
    instance_type
    "t3.medium"
    ipv6_address_count
    = (known after apply)
    ipv6_addresses
    (known after apply)

[^28]: EXPLORER
    . . .
    les.tf ..\\EC2 .
    .gitignore
    provider.tf U
    ec2.tf ..\\va
    V REPOS
    terraform > variables > roboshop.tfvars > _ instance_type
    > Ansible
    1 instance_type = "t3. small"
    > Concepts
    > notes
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    terraform
    > session1
    variables
    > .terraform
    E .terraform.lock.hcl
    U
    ec2.tf
    U
    provider.tf
    U
    roboshop.tfvars
    sg.tf
    U
    {} terraform.tfstate
    E terraform.tfstate.backup
    terraform.tfvars
    variables.tf
    U
    gitignore

[^29]: PS E: \\AWSDevOps \\Repos \\terraform\\variables> terraform plan -var-file="roboshop. tfvars"
    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    + create
    Terraform will perform the following actions:
    # aws_instance. web will be created
    + resource "aws_instance" "web" {
    + ami
    "ami -Of3c7d07486cad139"
    arn
    = (known after apply)
    + associate_public_ip_address
    = (known after apply)
    + availability_zone
    = (known after apply)
    +
    cpu_core_count
    = (known after apply)
    + cpu_threads_per_core
    = (known after apply)
    disable_api_stop
    = (known after apply)
    disable_api_termination
    = (known after apply)
    ebs_optimized
    = (known after apply)
    + get_password_data
    = false
    + host id
    = (known after apply)
    + host_resource_group_arn
    = (known after apply)
    + iam_instance_profile
    = (known after apply)
    + id
    = (known after apply)
    instance_initiated_shutdown_behavior = (known after apply)
    instance_lifecycle
    = (known after apply)
    + instance_state
    = (known after apply)
    + instance_type
    E
    "t3. large" -
    + ipv6_address_count
    = (known after apply)
    ipv6_addresses
    = (known after apply)

[^30]: C: \\devops \\daws-76s\\repos \\terraform>set TF_VAR_instance_type=t3. xlarge
    C: \\devops\\daws-76s \\repos\\terraform>cd variables
    C: \\devops\\daws-76s\\repos\\terraform\\variables>terraform plan

[^31]: C: \\devops\\daws-76s\\repos \\terraform\\variables>terraform plan -var-file="roboshop. tfvars" -var="instance_type=t3. medium

[^32]: terraform > variables > variables.tf > ..
    1
    # 1. command line
    2
    # 2. -var-file
    3
    # 3. terraform . tfvars
    14
    # 4. ENV variables

