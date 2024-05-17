---
title: 28Day_Terraform
uuid: d85dab74-1404-11ef-a737-9a665e06d35f
version: 407
created: '2024-05-17T09:50:51+05:30'
tags:
  - terraform
---

\

***Topics:***

1. *<mark style="background-color:#f8d616;">Multiple environments<!-- {"backgroundCycleColor":"25"} --></mark>*

      1. tfvars

      2. workspaces

      3. Different Repos completely

\

\

*<mark style="background-color:#f8914d;">**Multiple environments:**<!-- {"backgroundCycleColor":"24"} --></mark>*

\

How to create multiple environments with terraform? There are multiple ways

      1. tfvars

      2. workspaces

      3. Different Repos completely

\

# <mark style="background-color:#f8914d;">**tfvars**<!-- {"backgroundCycleColor":"24"} --></mark>

\

create a new repo - **terraform-multi-env**

![d0b7341b-d34b-4e11-8ff8-d56a9af085e7.png|913.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/d0b7341b-d34b-4e11-8ff8-d56a9af085e7.png) [^1]

\

Also new folder in VS - **terraform-multi-env**

![773e5217-1674-4373-abc9-0c0de65187a6.png|803](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/773e5217-1674-4373-abc9-0c0de65187a6.png) [^2]

\

subfolder -tfvars

![](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/6f758922-631a-4bad-841e-8766f10eb04a.png) [^3]

\

![06c3207a-6acc-4d61-a922-6ed806566f22.png|811](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/06c3207a-6acc-4d61-a922-6ed806566f22.png) [^4]

\

\

Create separate folders for dev & prod environments

![](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/9bd3b01b-d60b-4275-b465-d79bd3ccea84.png) [^5]

\

\

Create different S3 buckets to maintain state for development, UAT, Testing, PROD.

\

[**chilops-terraform-s3-dev**](https://us-east-1.console.aws.amazon.com/s3/buckets/chilops-terraform-s3-dev?region=us-east-1&bucketType=general)     -- Bucket for development

[**chilops-terraform-s3-prod**](https://us-east-1.console.aws.amazon.com/s3/buckets/chilops-terraform-s3-prod?region=us-east-1&bucketType=general)   -- Bucket for production 

\

![d4d3d323-a403-48ff-a9be-155622ebe84b.png|884.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/d4d3d323-a403-48ff-a9be-155622ebe84b.png) [^6]

\

creating DynamoDB - table creation for locking

\

\

![0c8a72af-b414-46c4-9304-828e66191571.png|712.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/0c8a72af-b414-46c4-9304-828e66191571.png) [^7]

\

[**chilops-locking-dev**](https://us-east-1.console.aws.amazon.com/dynamodbv2/home?region=us-east-1#table?name=chilops-locking-dev)     -- locking table for Dev

[**chilops-locking-prod**](https://us-east-1.console.aws.amazon.com/dynamodbv2/home?region=us-east-1#table?name=chilops-locking-prod)   -- locking table for Prod 

![83179178-1a34-4c3c-b341-7ceeb43e5020.png|845.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/83179178-1a34-4c3c-b341-7ceeb43e5020.png) [^8]

\

\

Under Dev - backend.tf code

```
bucket = "chilops-terraform-s3-dev"
key = "multienv"
region = "us-east-1"
dynamodb_table = "chilops-locking-dev"
```

\

<mark style="background-color:#f8914d;">**IMP node: for every terraform project use different keyname "mulitenv" else it will merge... any name is fine**<!-- {"backgroundCycleColor":"24"} --></mark>

![20925e84-fdc8-42a4-bf7d-fce01435286f.png|807](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/20925e84-fdc8-42a4-bf7d-fce01435286f.png) [^9]

\

Under prod - backend.tf code

\

```
bucket = "chilops-terraform-s3-prod"
key = "multienv"
region = "us-east-1"
dynamodb_table = "chilops-locking-prod"
```

  

![0ba574c0-109f-44e5-b05b-276274131514.png|801](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/0ba574c0-109f-44e5-b05b-276274131514.png) [^10]

\

data.tf code

![d452b6f9-7173-40db-af54-5a28051bbaf3.png|785](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/d452b6f9-7173-40db-af54-5a28051bbaf3.png) [^11]

\

roboshop.tf code   -- In this code **startwith function** is used.

![280317df-f9b8-44b4-a714-8b88c0fe907b.png|844](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/280317df-f9b8-44b4-a714-8b88c0fe907b.png) [^12]

\

under dev - **dev.tfvars code**

```
instance_names = {
    mongodb-dev = "t3.small"
    redis-dev = "t2.micro"
    mysql-dev = "t3.small"
    web-dev = "t2.micro"

}
```

   

![64655ac9-0b37-4064-8c5c-cfb80eba8cff.png|788](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/64655ac9-0b37-4064-8c5c-cfb80eba8cff.png) [^13]

\

under prod - **prod.tfvars code**

```
instance_names = {
    mongodb-prod = "t3.small"
    redis-prod = "t2.micro"
    mysql-prod = "t3.small"
    web-prod = "t2.micro"

}
```

![20bded51-826b-4397-acfd-c437ded6511f.png|785](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/20bded51-826b-4397-acfd-c437ded6511f.png) [^14]

\

provider.tf code

![08e21dcb-b023-423b-9715-1652852baf83.png|821.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/08e21dcb-b023-423b-9715-1652852baf83.png) [^15]

\

variables.tf code

![38bf8c41-28f1-4330-84d1-a2914583aec1.png|786](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/38bf8c41-28f1-4330-84d1-a2914583aec1.png) [^16]

```
terraform init -backend-config=dev/backend.tf
```

![810cb566-f9f6-418b-ad13-9951897899f2.png|790](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/810cb566-f9f6-418b-ad13-9951897899f2.png) [^17]

\

```
terraform plan -var-file=dev/dev.tfvars
```

\

![8d6309e0-1e1b-42ba-b232-0d8d9cfaa0d9.png|713](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/8d6309e0-1e1b-42ba-b232-0d8d9cfaa0d9.png) [^18]

![c3ad682f-48db-421c-945a-822ff444b9d4.png|708](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/c3ad682f-48db-421c-945a-822ff444b9d4.png) [^19]

\

\

**Dev** instances are created:

![d6a8715f-da55-4ab5-87a6-765d36d5f9d9.png|797.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/d6a8715f-da55-4ab5-87a6-765d36d5f9d9.png) [^20]

\

\

\

![2be26fb9-48a6-48c5-a1f8-bd9c89dc116e.png|995.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/2be26fb9-48a6-48c5-a1f8-bd9c89dc116e.png) [^21]

\

Now doing same in **PROD** environment: " -reconfigure needs to be used when we start doing in other environments like PROD, UAT etc

\

<mark style="background-color:#f8d616;">I**MP: we are switching to different envronments from dev to prod or prod to UAT then every time we need to reinitialize using**<!-- {"backgroundCycleColor":"25"} --></mark> <mark style="background-color:#f8914d;">**-reconfigure**<!-- {"backgroundCycleColor":"24"} --></mark>

```
terraform init -reconfigure -backend-config=prod/backend.tf
```

![5503fb29-b567-4d17-a47d-aa7ef2fe14aa.png|773](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/5503fb29-b567-4d17-a47d-aa7ef2fe14aa.png) [^22]

\

```
terraform plan -var-file=prod/prod.tfvars
```

![b103c855-8656-4632-acfc-698daaf866c6.png|784](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/b103c855-8656-4632-acfc-698daaf866c6.png) [^23]

![eb79f870-c065-4e2d-bb23-7e99ab8911d1.png|782](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/eb79f870-c065-4e2d-bb23-7e99ab8911d1.png) [^24]

\

```
terraform apply -var-file=prod/prod.tfvars
```

![77cedda5-52b7-488f-83db-37ba7a11a9c9.png|704](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/77cedda5-52b7-488f-83db-37ba7a11a9c9.png) [^25]

\

\

Now PROD instances launched & running

\

![b098b909-6bd9-43c5-9cf9-92ce69687034.png|872.3333740234375](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/b098b909-6bd9-43c5-9cf9-92ce69687034.png)

\

To destroy DEV & PROD env

<mark style="background-color:#f8d616;">I**MP: we are switching to different envronments from dev to prod or prod to UAT then every time we need to reinitialize using**<!-- {"backgroundCycleColor":"25"} --></mark> <mark style="background-color:#f8914d;">**-reconfigure**<!-- {"backgroundCycleColor":"24"} --></mark>

```
terraform destroy -var-file=prod/prod.tfvars
terraform init -reconfigure -backend-config=dev/backend.tf
terraform destroy -var-file=dev/dev.tfvars
```

![](https://images.amplenote.com/d85dab74-1404-11ef-a737-9a665e06d35f/47e64a45-8032-4fc5-bee3-31c7f0e568db.png)

\

\

# <mark style="background-color:#f8914d;">**workspaces**<!-- {"backgroundCycleColor":"24"} --></mark>

[^1]: G
    https://github.com/new
    =
    New repository
    Q Type to search
    Create a new repository
    A repository contains all project files, including the revision history. Already have a project repository elsewhere?
    Import a repository.
    Required fields are marked with an asterisk (\*).
    Owner \*
    Repository name \*
    environment
    environmental
    chilops
    terraform-multi-env
    terraform-multi-env is available.
    Great repository names are short and memorable. Need inspiration? How about congenial-octo-fortnight ?
    Description (optional)
    O
    Public
    Anyone on the internet can see this repository. You choose who can commit.
    Private
    You choose who can see and commit to this repository.

[^2]: V
    REPOS
    Li Li O @ Concepts > ! person.yaml
    > Ansible
    -
    name: sivakumar
    Concepts
    N
    dob: "2023-09-09"
    3
    Ansible.MD
    M
    address :
    4
    address-line1: vivek street
    image-1.png
    5
    address-line2: sanath nagar
    image.png
    6
    city : HYD
    {} person.json
    M
    email: info@joindevops . com
    person.xml
    18
    ! person.yaml
    9
    -
    name: ramesh
    notes
    10
    dob: "2022-09-08"
    11
    address :
    > Robosho-shellscripts
    M
    12
    -
    address-line1: vivek street1
    > roboshop-ansible
    13
    address-line2: sanath nagar1
    > roboshop-ansible-roles
    14
    city : HYD1
    > shellscripts
    15
    address-line1: vivek street2
    > terraform
    16
    address-line2: sanath nagar2
    terraform-multi-env
    17
    city : HYD2
    18
    email: info@joindevops . com

[^3]: > terraform-multi-env \\ tfvars

[^4]: mongodb-dev, redis-dev
    mongodb-dev . daws 76s . online
    same code but different configuration

[^5]: v terraform-multi-env \\ tfvars
    > dev
    > prod
    data.tf
    provider.tf
    CC CC
    roboshop.tf
    variables.tf

[^6]: General purpose buckets
    Directory buckets
    General purpose buckets (3) Info
    ALL AWS Regions
    C
    Copy ARN
    Empty
    Delete
    Create bucket
    Buckets are containers for data stored in $3.
    Find buckets by name
    <
    1
    Name
    AWS Region
    IAM Access Analyzer
    Creation date
    D
    O
    chilops-terraform-remotestate
    US East (N. Virginia) us-east-1
    View analyzer for us-east-1
    May 16, 2024, 13:03:47 (UTC+05:30)
    O
    chilops-terraform-s3-dev
    US East (N. Virginia) us-east-1
    View analyzer for us-east-1
    May 17, 2024, 10:35:59 (UTC+05:30)
    O
    chilops-terraform-s3-prod
    US East (N. Virginia) us-east-1
    View analyzer for us-east-1
    May 17, 2024, 10:33:29 (UTC+05:30)

[^7]: DynamoDB > Tables > Create table
    Create table
    Table details Info
    DynamoDB is a schemaless database that requires only a table name and a primary key when you create the table.
    Table name
    This will be used to identify your table.
    chilops-locking-dev
    Between 3 and 255 characters, containing only letters, numbers, underscores (_), hyphens (-), and periods (.).
    Partition key
    The partition key is part of the table's primary key. It is a hash value that is used to retrieve items from your table and allocate data across
    hosts for scalability and availability.
    LockID
    String
    1 to 255 characters and case sensitive.
    Sort key - optional
    You can use a sort key as the second part of a table's primary key. The sort key allows you to sort or search among all items sharing the
    same partition key.
    Enter the sort key name
    String
    1 to 255 characters and case sensitive.

[^8]: DynamoDB > Tables
    Tables (3) Info
    C
    Actions
    Delete
    Create table
    Q Find tables by table name
    Any tag key
    Any tag value
    <
    1
    O
    Name
    Status
    Partition key
    Sort key
    Indexes
    Deletion protection
    Read capacity mode
    Write capacity
    O
    chilops-locking
    Active
    LockID (S)
    0
    Off
    Provisioned (1)
    Provisioned (1)
    O
    chilops-locking-dev
    Active
    LockID (S)
    0
    Off
    Provisioned (5)
    Provisioned (5)
    0
    chilops-locking-prod - Active
    LockID (S)
    0
    Off
    Provisioned (5)
    Provisioned (5)

[^9]: V
    REPOS
    terraform-multi-env > tfvars > dev > backend.tf > ...
    > Ansible
    1
    bucket = "chilops-terraform-s3-dev"
    Concepts
    2
    key = "mutlienv"
    3
    Ansible.MD
    region = "us-east-1"
    M
    4
    dynamodb_table = "chilops-locking-dev"
    image-1.png
    5
    image.png
    {} person.json
    M
    person.xml
    ! person.yaml
    > notes
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    v terraform-multi-env \\ tivars
    > .terraform
    dev
    backend.tf
    -
    4. U

[^10]: REPOS
    terraform-multi-env > tfvars > prod > backend.tf > . bucket
    > Ansible
    1
    bucket = "chilops-terraform-s3-prod"
    Concepts
    2
    key = "multienv"
    3
    Ansible.MD
    region = "us-east-1"
    M
    4
    dynamodb_table = "chilops-locking-prod"
    image-1.png
    15
    image.png
    16
    {} person.json
    M
    person.xml
    ! person.yaml
    > notes
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    terraform-multi-env \\ tivars
    > .terraform
    dev
    backend.tf
    4, U
    dev.tfvars
    U
    v prod
    O
    backend.tf
    4. U

[^11]: terraform-multi-env > tivars > data.tf > { data "aws_vpc" "default"
    1
    data "aws_ami" "centos8"{
    2
    owners = \["973714476881"\]
    3
    most_recent
    = true
    4
    5
    filter {
    6
    name
    "name"
    7
    values = \["Centos-8-Devops-Practice"\]
    8
    9
    10
    filter {
    11
    name
    = "root-device-type"
    12
    values = \["ebs"\]
    13
    14
    15
    filter {
    16
    name
    "virtualization-type"
    17
    values = \["hvm" \]
    18
    19
    20
    21
    data "aws_ami" "aws-linux-2"{
    22
    owners = \["amazon" \]
    23
    most_recent
    = true
    24
    25
    filter {
    26
    name
    = "name"
    27
    values = \["amzn2-ami-kernel-5 . 10-hvm-\*"\]
    28
    29
    30
    filter {
    31
    name
    "root-device-type"
    32
    values = \["ebs"\]
    33
    34
    35
    filter {
    36
    name
    = "virtualization-type"
    37
    values = \["hvm" \]
    38
    LP
    39
    40
    41
    42
    data "aws_vpc" "default" {
    43
    default = true
    44

[^12]: REPOS
    terraform-multi-env > tfvars > roboshop.f > % resource "aws_route53_record" "www" > \[ \] records > \[e\] 0
    > Ansible
    1
    resource "aws_instance" "web" {
    Concepts
    2
    for_each = var . instance_names
    3
    Ansible.MD
    ami
    M
    = data . aws_ami . centos8. id
    instance_type = each . value
    image-1.png
    15
    tags = {
    image.png
    6
    Name = each . key
    {} person.json
    M
    7
    }
    person.xml
    8
    ! person.yaml
    19
    10
    > notes
    11
    > Robosho-shellscripts
    resource "aws_route53_record" "www" {
    M
    12
    for_each = aws_instance . web
    > roboshop-ansible
    13
    zone_id = var . zone_id
    > roboshop-ansible-roles
    14
    name
    = "${each . key} . ${var . domain_name}" #interpolation
    > shellscripts
    15
    type
    = "A"
    > terraform
    16
    tt1
    = 1
    v terraform-multi-env \\ tivars
    17
    records = \[startswith(each. key, "web") ? each . value. public_ip : each. value . private_ip \]
    18
    dev
    19
    backend.tf
    2, U
    20
    # output "instances_info" {
    dev.tfvars
    U
    21
    #
    value = aws_instance . web
    prod
    22
    #
    backend.tf
    2, U
    prod.tfvars
    U

[^13]: > Ansible
    instance_names = {
    Concepts
    2
    mongodb-dev = "t3. small"
    3
    Ansible.MD
    M
    redis-dev = "t2.micro"
    4
    mysql-dev = "t3. small"
    image-1.png
    15
    web-dev = "t2.micro"
    image.png
    16
    {} person.json
    M
    7
    person.xml
    8
    ! person.yaml
    > notes
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    v terraform-multi-env \\ tivars
    dev
    backend.tf
    2, U
    dev.tfvars
    U

[^14]: REPOS
    terraform-multi-env > tfvars > prod > prod.tfvars > do instance_names
    > Ansible
    1
    instance_names = {
    Concepts
    2
    mongodb-prod = "t3. small"
    3
    Ansible.MD
    M
    redis-prod = "t2.micro"
    4
    mysql-prod = "t3. small"
    image-1.png
    5
    web-prod = "t2.micro"
    image.png
    6
    {} person.json
    M
    person.xml
    ! person.yaml
    > notes
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    v terraform-multi-env \\ tivars
    dev
    backend.tf
    2, U
    dev.tfvars
    U
    prod
    backend.tf
    2, U
    prod.tfvars
    U

[^15]: REPOS
    terraform-multi-env > tivars > provider.tf > > provider "aws"
    > Ansible
    1
    terraform {
    Concepts
    2
    required_providers {
    3
    Ansible.MD
    M
    aws = {
    4
    source = "hashicorp/aws"
    image-1.png
    15
    version = "5.31.0" # AWS provider version, not terraform version
    image.png
    16
    {} person.json
    M
    7
    person.xml
    18
    ! person.yaml
    19
    backend "s3" {
    notes
    10
    #
    bucket = "chilops-terraform-remotestate"
    11
    #
    > Robosho-shellscripts
    key
    = "dynamic"
    M
    12
    #
    region = "us-east-1"
    > roboshop-ansible
    13
    dynamodb_table = "chilops-locking"
    > roboshop-ansible-roles
    14
    > shellscripts
    15
    > terraform
    16
    v terraform-multi-env \\ tivars
    17
    provider "aws" {
    18
    > .terraform
    region = "us-east-1"
    19
    dev
    backend.tf
    4. U
    dev.tfvars
    U
    prod
    O
    backend.tf
    4, U
    prod.tfvars
    U
    E .terraform.lock.hcl
    U
    data.tf
    U
    provider.tf
    U

[^16]: EXPLORER
    . . .
    provider.tf .\\tfvars U
    provider.tf .. \\dynamic
    roboshop.tf U .
    REPOS
    terraform-multi-env > tivars > variables.tf > % variable "domain_name"
    > Ansible
    1
    variable "instance_names" {
    N
    Concepts
    type = map
    3
    Ansible.MD
    #
    M
    default = {
    mongodb = "t3. small"
    image-1.png
    15
    #
    redis = "t2.micro"
    image.png
    6
    mysql = "t3. small"
    {} person.json
    M
    7
    #
    person.xml
    8
    ! person.yaml
    9
    > notes
    10
    O
    variable "zone_id" {
    11
    default = "Z06431971951XUVZELNIC"
    > Robosho-shellscripts
    M
    12
    > roboshop-ansible
    13
    > roboshop-ansible-roles
    14
    variable "domain_name" {
    > shellscripts
    15
    default = "chowdarychilukuri. in"
    > terraform
    16
    }
    v terraform-multi-env \\ tivars
    > .terraform
    dev
    backend.tf
    4. U
    dev.tfvars
    U
    prod
    backend.tf
    4. U
    prod.tfvars
    U
    E .terraform.lock.hcl
    U
    data.tf
    U
    provider.tf
    U
    roboshop.tf
    U
    variables.tf
    U

[^17]: chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform-multi-env/tfvars (main)
    $ terraform init -backend-config=dev/backend. tf
    Initializing the backend. . .
    Initializing provider plugins . . .
    Finding hashicorp/aws versions matching "5. 31.0"...
    Installing hashicorp/aws v5 . 31.0. . .
    Installed hashicorp/aws v5. 31.0 (signed by Hashicorp)
    Terraform has created a lock file . terraform. lock.hc1 to record the provider
    selections it made above. Include this file in your version control repository
    so that Terraform can guarantee to make the same selections by default when
    you run "terraform init" in the future.
    Terraform has been successfully initialized!
    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. Al1 Terraform commands
    should now work.
    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform-multi-env/tfvars (main)
    $

[^18]: chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform-multi-env/tfvars (main)
    $ terraform plan -var-file=dev/dev . tfvars
    Acquiring state lock. This may take a few moments . . .
    data . aws_vpc . default: Reading. . .
    data . aws_ami . centos8: Reading. . .
    data . aws_ami . aws-linux-2: Reading. . .
    data . aws_ami . centos8: Read complete after 1s \[id=ami-Of3c7d07486cad139\]
    data . aws_ami . aws-linux-2: Read complete after 1s \[id=ami-04ff98ccbfa41c9ad\]
    data . aws_vpc . default: Read complete after 2s \[id=vpc-0817cae8968304c06\]
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols:
    + create
    Terraform will perform the following actions :
    # aws_instance . web \["mongodb-dev"\] will be created
    +
    resource "aws_instance" "web" {
    +
    ami
    = "ami -Of 3c7 d07486cad139"
    +
    arn
    (known after apply)
    +
    associate_public_ip_address
    E
    (known after apply)
    +
    availability_zone
    = (known after apply)
    cpu_core_count
    (known after apply)
    +
    cpu_threads_per_core
    E
    (known after apply)

[^19]: #
    aws_route53_record . www\["web-dev"\] will be created
    +
    resource "aws_route53_record" "www" {
    +
    allow_overwrite = (known after apply)
    +
    fadn
    : (known after apply)
    +
    id
    E
    (known after apply)
    +
    name
    "web-dev . chowdarychi lukuri . in"
    +
    records
    (known after apply)
    +
    tt1
    =1
    +
    type
    "A"
    +
    zone_id
    "Z06431971951XUVZELNIC"
    Plan: 8 to add, 0 to change, 0 to destroy.
    Note: You didn't use the -out option to save this plan, so Terraform can't
    guarantee to take exactly these actions if you run "terraform apply" now.
    Releasing state lock. This may take a few moments. . .
    chowd@chowdary MINGW64 /e/awsdevops /Repos /terraform-multi-env/tfvars (main)

[^20]: aws
    Services
    Q Search
    \[Alt+S\]
    4
    ?
    N. Virginia v
    chowdary
    DEC2
    Route 53
    IAM
    VPC
    $3
    DynamoDB
    Instances (4) Info
    C
    Connect
    Instance state
    Actions
    Launch instances
    EC2 Dashboard
    X
    EC2 Global View
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    Events
    Instance state = running \|X
    Clear filters
    < 1 >
    Console-to-Code Preview
    O
    Name _
    A
    Instance ID
    Instance state
    A
    Instance type
    4
    Status check
    Alarm status
    Availability Zo
    Instances
    0
    web-dev
    i-0ad4355100d383cb9
    Running
    t2.micro
    Initializing
    View alarms +
    us-east-1d
    Instances
    0
    redis-dev
    i-08db 7ae3afd15cf3f
    Running
    t2.micro
    Initializing
    View alarms +
    us-east-1d
    Instance Types
    0
    mysql-dev
    i-05a565586b3781a29
    Running
    t3.small
    Initializing
    View alarms +
    us-east- 1a
    Launch Templates
    mongodb-dev
    i-0c31bcd2e6265b488
    Running
    t3.small
    Initializing
    View alarms +
    us-east-1a
    Spot Requests

[^21]: EC2
    Route 53
    8: IAM
    VPC
    S3
    DynamoDB
    Amazon S3
    X
    Amazon S3 > Buckets > chilops-terraform-s3-dev
    Buckets
    chilops-terraform-s3-dev info
    Access Grants
    Access Points
    Objects
    Properties
    Permissions
    Metrics
    Management
    Access Points
    Object Lambda Access Points
    Multi-Region Access Points
    Batch Operations
    Objects (1) Info
    IAM Access Analyzer for $3
    C
    Copy S3 URI
    Copy URL
    Download
    Open \[
    Delete
    Actions
    Create folder
    Upload
    Objects are the fundamental entities stored in Amazon $3. You can use Amazon S3 inventory \[ to get a list of all objects in your bucket. For others to access your objects, you'll need to
    explicitly grant them permissions. Learn more \[Z
    Block Public Access settings for
    this account
    Q Find objects by prefix
    <
    1
    7Storage Lens
    Name
    Type
    Last modified
    4
    Size
    4
    Storage class
    Dashboards
    D mutlienv
    May 17, 2024, 11:49:36
    20.7 KB
    Standard
    Storage Lens groups
    (UTC+05:30)
    AWS Organizations settings

[^22]: chowd@chowdary MINGW64 /e/awsdevops/Repos /terraform-multi-env/tfvars (main)
    $ terraform init -reconfigure -backend-config=prod/backend. tf
    Initializing the backend. ..
    Successfully configured the backend "s3"! Terraform will automatically
    use this backend unless the backend configuration changes.
    Initializing provider plugins. . .
    Reusing previous version of hashicorp/aws from the dependency lock file
    Using previously-installed hashicorp/aws v5 . 31.0
    Terraform has been successfully initialized!
    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. Al1 Terraform commands
    should now work.
    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.

[^23]: chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform-multi-env/tfvars (main)
    $ terraform plan -var-file=prod/prod. tfvars
    Acquiring state lock. This may take a few moments. . .
    data . aws_vpc . default: Reading. . .
    data . aws_ami . centos8: Reading. . .
    data . aws_ami . aws-linux-2: Reading. . .
    data . aws_ami . centos8: Read complete after 2s \[id=ami-Of3c7d07486cad139\]
    data. aws_ami . aws -linux-2: Read complete after 2s \[id=ami-04ff98ccbfa41c9ad\]
    data . aws_vpc . default: Read complete after 3s \[id=vpc-0817cae8968304c06\]
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols:
    +
    create
    Terraform will perform the following actions :
    # aws_instance . web \["mongodb-prod"\] will be created
    +
    resource "aws_instance" "web"

[^24]: Plan: 8 to add, 0 to change, 0 to destroy.
    Note: You didn't use the -out option to save this plan, so Terraform can't
    guarantee to take exactly these actions if you run "terraform apply" now.
    Releasing state lock. This may take a few moments. . .
    chowd@chowdary MINGW64 /e/awsdevops /Repos /terraform-multi-env/tfvars (main)

[^25]: $ terraform apply -var-file=prod/prod. tfvars
    Acquiring state lock. This may take a few moments . . .
    data . aws_vpc . default: Reading. . .
    data . aws_ami . aws-linux-2: Reading. . .
    data . aws_ami . centos8: Reading. . .
    data . aws_ami . centos8: Read complete after 1s \[id=ami-Of3c7d07486cad139\]
    data . aws_ami . aws-linux-2: Read complete after 1s \[id=ami-04ff98ccbfa41c9ad\]
    data . aws_vpc . default: Read complete after 2s \[id=vpc-0817cae8968304c06\]
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols :
    +
    create
    Terraform will perform the following actions:
    # aws_instance . web \["mongodb-prod"\] will be created
    +
    resource "aws_instance" "web"
    {
    +
    ami
    "ami-Of 3c7 d07486cad139"
    +
    arn
    (known after apply)
    +
    associate_public_ip_address
    =
    (known after apply)
    +
    availability_zone
    (known after apply)
    +
    cpu_core_count
    (known after apply)
    +
    cpu_threads_per_core
    E
    (known after apply)

