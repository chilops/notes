---
title: 29Day_Terraform
uuid: f63d379e-1d79-11ef-a7bb-2e97089a9920
version: 620
created: '2024-05-29T10:41:52+05:30'
tags:
  - terraform
---

***Topics:***

1. *<mark style="background-color:#f8d616;">Modules development - Important topic<!-- {"backgroundCycleColor":"25"} --></mark>*

1. <mark style="background-color:#f3de6c;">VPC - Virtual private cloud<!-- {"backgroundCycleColor":"14"} --></mark>

1. <mark style="background-color:#f8d616;">CIDR -<!-- {"backgroundCycleColor":"25"} --></mark><mark style="background-color:#f8914d;">**classless interdomain routing**<!-- {"backgroundCycleColor":"24"} --></mark>

\

\

\

# *<mark style="background-color:#f8914d;">**Modules** development **- Important topic (its like a functions concept)**<!-- {"backgroundCycleColor":"24"} --></mark>*

DRY - Don't repeat yourself.

**code re-use** -- no need to write infra for every project from the scratch.

\

**Modules are of two types.**

1. **Customized modules** - For specific organization/company (cloud central team or cloud owners or cloud managed teams - these team will develop/write the code & they use it for their organization)<!-- {"indent":1} -->

    1. **Open source modules -** Already pre-defined.

\

<mark style="background-color:#f3de6c;">**Customized modules:**<!-- {"backgroundCycleColor":"14"} --></mark>

Create below two folders and add .gitignore file

![](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/5395a5ed-8161-4d12-b19d-a5a79dd0e54f.png) [^1]

\

<mark style="background-color:#f3de6c;">Terraform level naming best practices<!-- {"backgroundCycleColor":"14"} --></mark>

![0cb6ae2f-cf17-4a27-99bf-147c2c8e0c01.png|726](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/0cb6ae2f-cf17-4a27-99bf-147c2c8e0c01.png) [^2]

![8153dc4c-0ec7-4f6a-8211-7df6d97d5599.png|630](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/8153dc4c-0ec7-4f6a-8211-7df6d97d5599.png) [^3]

\

<mark style="background-color:#f3de6c;">ec2.tf code<!-- {"backgroundCycleColor":"14"} --></mark>

![ce752384-19f5-4332-8a5e-3c22d7008c0b.png|770](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/ce752384-19f5-4332-8a5e-3c22d7008c0b.png) [^4]

\

variables.tf code

![35b4e6ec-fa8f-4148-a1d5-5a879d1aaf5e.png|768](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/35b4e6ec-fa8f-4148-a1d5-5a879d1aaf5e.png) [^5]

\

Now above files which are under **ec2** folder we can consider as modules(data), By using this code we can create multiple environments(dev, prod, uat etc) without writing extra code. As an example now creating one more folder called **roboshop-ec2** and use modules from **ec2** folder.

\

<mark style="background-color:#f3de6c;">create roboshop-ec2 folder<!-- {"backgroundCycleColor":"14"} --></mark> 

ec2.tf code 

![48a2d381-a2bd-44eb-87b2-428575a73d81.png|746](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/48a2d381-a2bd-44eb-87b2-428575a73d81.png) [^6]

\

variables.tf code

![8739a40d-d34b-4058-94ed-9c3d47091d5a.png|721.3333740234375](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/8739a40d-d34b-4058-94ed-9c3d47091d5a.png) [^7]

\

<mark style="background-color:#f3de6c;">provider.tf file always should be present in user projects but not in modules.<!-- {"backgroundCycleColor":"14"} --></mark>

providers.tf code

![a57f69ad-3ff1-4385-acfd-d2955ea16027.png|761.3333740234375](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/a57f69ad-3ff1-4385-acfd-d2955ea16027.png) [^8]

\

also add .gitignore file (this is useful to push to github)

![1c1b003a-3fa5-4530-abc0-10e6f7d2cedc.png|831](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/1c1b003a-3fa5-4530-abc0-10e6f7d2cedc.png) [^9]

\

```
terraform init
```

![b2879931-a27d-4dca-b75c-f8f5b6855c55.png|697](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/b2879931-a27d-4dca-b75c-f8f5b6855c55.png) [^10]

\

```
terraform plan
```

![7b262410-7798-45c4-8034-f22741421306.png|660](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/7b262410-7798-45c4-8034-f22741421306.png) [^11]

\

Now if you want to pass variables to specify t3.micro instead of t2.micro from the current module. so update code as below in ec2.tf code (it will override which is present in ec2 folder code).

\

ec2.tf code update

![dd9d9f25-20e1-4a20-889f-a3eb53a90edf.png|736](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/dd9d9f25-20e1-4a20-889f-a3eb53a90edf.png) [^12]

\

outputs.tf code

![03dd8981-720b-43d5-a4c0-18b2a6dc821b.png|801](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/03dd8981-720b-43d5-a4c0-18b2a6dc821b.png) [^13]

\

```
terraform plan
```

![702134d9-d122-43e5-9b48-80018074f5dc.png|687](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/702134d9-d122-43e5-9b48-80018074f5dc.png) [^14]

\

or we can use different way.. create variables.tf file

\

variables.tf code

![77f867b2-3bda-4904-93cd-9be1e7b04cef.png|747](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/77f867b2-3bda-4904-93cd-9be1e7b04cef.png) [^15]

\

updated ec2.tf code

![7fab92a0-e014-41b6-b9a2-07af5563d503.png|724](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/7fab92a0-e014-41b6-b9a2-07af5563d503.png) [^16]

\

```
terraform plan
```

\

![40be1215-77b4-4f88-9b15-2733e77709d6.png|639](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/40be1215-77b4-4f88-9b15-2733e77709d6.png) [^17]

\

1\. **module developer** -- Who develops modules

2\. **module user**          -- Who consumes modules

\

\

outputs.tf code in roboshop-ec2

![c4ff3c59-0eb8-44a2-92b5-83bf11ad6d60.png|737](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/c4ff3c59-0eb8-44a2-92b5-83bf11ad6d60.png) [^18]

\

```
terraform plan
```

![79a9ffe7-fe1c-494e-94e7-e6fbe036e547.png|749](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/79a9ffe7-fe1c-494e-94e7-e6fbe036e547.png) [^19]

\

```
terraform apply -auto-approve
```

![93b60081-09a8-4925-ba14-806f369f3d55.png|902](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/93b60081-09a8-4925-ba14-806f369f3d55.png) [^20]

\

\

![93b60081-09a8-4925-ba14-806f369f3d55.png|902](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/93b60081-09a8-4925-ba14-806f369f3d55.png) [^21]

\

![12cc74da-a426-4f7b-9eee-ae58c30ebec2.png|907.3333740234375](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/12cc74da-a426-4f7b-9eee-ae58c30ebec2.png) [^22]

\

```
terraform destroy -auto-approve
```

![5beda3dc-5ccc-49f1-9bff-14822f0519f2.png|938](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/5beda3dc-5ccc-49f1-9bff-14822f0519f2.png) [^23]

\

# <mark style="background-color:#f8914d;">**VPC - Virtual private cloud -**<!-- {"backgroundCycleColor":"24"} --></mark> Its an Isolated network within AWS

\

![3213a741-25d1-42ff-9677-f6206567115a.png|384](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/3213a741-25d1-42ff-9677-f6206567115a.png) [^24]

\

![474eb676-fb4b-4036-8685-88d1489101f1.png|756](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/474eb676-fb4b-4036-8685-88d1489101f1.png) [^25]

\

\

Arch -- Entry point = Internet gateway

Roads -- Routes 

\

![bb777bee-cb38-41e2-ac14-e24d20db55e0.png|799](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/bb777bee-cb38-41e2-ac14-e24d20db55e0.png) [^26]

**private & public subnets:**

Public affairs     -- Direct access  (web servers)

Minister offices  -- No direct access (shipping, payment servers)

PM office           -- No direct access (DB servers)

\

![c2c05fa8-4b50-434f-bd89-1bc418f5c597.png|782](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/c2c05fa8-4b50-434f-bd89-1bc418f5c597.png) [^27]

\

**Route tables --  routes**

Public route table       --   routes --  attach with public subnets

Private route table      --   routes --  attach with private subnets

Database route table  --   routes --  attach with database subnets

\

\

# <mark style="background-color:#f8914d;">**CIDR - classless interdomain routing**<!-- {"backgroundCycleColor":"24"} --></mark>

IPV4 --  192.168.1.1 --  32 bits = 4 octets

\

0 1 2 3 4 5 6 7 8 9 --- 10 numbers (decimals)

only 0,1 --  2 numbers (Binary)

\

**Decimal to Binary conversion**

7 6 5 4 3 2 1 0

\-  -  -  -  -  - -  - 8 bits in one octet.

\

1st -- 2^0 = 1

2nd -- 2^1 = 2

3rd -- 2^2 = 4

                = 8

                = 16

                = 32

                = 64 

8th -- 2^7 = 128

\

**1+2+4+8+16+32+64+128 = 255**

\

**192.168.1.1** 

\

192             168           1               1

11000000\.10101000.00000001.00000001

\

below calculation is for 168

2^3 = 8

2^5 = 32

2^7 = 128

\

![a17b79c6-b342-4bf5-a5fc-c3bc0f0a0f7d.png|703](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/a17b79c6-b342-4bf5-a5fc-c3bc0f0a0f7d.png) [^28]

\

![](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/a1a65fa9-5b02-4ea4-aa67-2b35a04a6d86.png) [^29]

we can create 4 billion(403 crores) of IP address we can use for create networks/servers

\

2^16 = 65536 IP addresses to create networks/servers

![a884ca8d-8e96-4156-bae8-d9801dcad63e.png|875.3333740234375](https://images.amplenote.com/f63d379e-1d79-11ef-a7bb-2e97089a9920/a884ca8d-8e96-4156-bae8-d9801dcad63e.png) [^30]

\

1:02:39

[^1]: terraform-modules
    > ec2 -
    gitignore
    U

[^2]: Naming conventions
    General conventions
    There should be no reason to not follow at least these conventions :)
    i
    Beware that actual cloud resources often have restrictions in allowed names. Some resources,
    for example, can't contain dashes, some must be camel-cased. The conventions in this book
    refer to Terraform names themselves.
    1. Use _ (underscore) instead of - (dash) everywhere (in resource names, data source names,
    variable names, outputs, etc).
    2. Prefer to use lowercase letters and numbers (even though UTF-8 is supported).

[^3]: Resource and data source arguments
    1. Do not repeat resource type in resource name (not partially, nor completely):
    \`resource "aws_route_table"
    "public" {}'
    A
    \`resource "aws_route_table" "public_route_table" {}'
    \`resource "aws_route_table" "public_aws_route_table" {}'

[^4]: REPOS
    terraform-modules > ec2 > ec2.tf > % resource "aws_instance" "module"
    > Ansible
    H
    resource "aws_instance" "module" {
    Concepts
    ami = var . ami
    13
    Ansible.MD
    M
    instance_type = var . instance_type
    4
    tags = var . tags
    image-1.png
    5
    image.png
    {} person.json
    M
    person.xml
    ! person.yaml
    notes
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    v terraform-modules
    v ec2
    ec2.tf
    U

[^5]: V REPOS
    terraform-modules > ec2 > variables.tf > < variable "tags"
    > Ansible
    1
    variable "ami" {
    Concepts
    default = "ami-Of3c7d07486cad139"
    3
    Ansible.MD
    M
    type = string
    4
    image-1.png
    15
    image.png
    6
    variable "instance_type" {
    {} person.json
    M
    7
    default = "t2.micro"
    person.xml
    8
    type = string
    ! person.yaml
    9
    10
    > notes
    11
    variable "tags" {
    > Robosho-shellscripts
    M
    12
    default = {}
    > roboshop-ansible
    13
    type = map
    > roboshop-ansible-roles
    14
    > shellscripts
    > terraform
    terraform-modules
    v ec2
    ec2.tf
    U
    variables.tf
    U

[^6]: V REPOS
    terraform-modules > roboshop-ec2 > \\ ec2.tf > ...
    > Ansible
    1
    module "roboshop_ec2" {
    Concepts
    2
    source = " . ./ec2"
    3
    Ansible.MD
    M
    14
    image-1.png
    image.png
    6
    {} person.json
    M
    7
    person.xml
    8
    ! person.yaml
    9
    10
    > notes
    11
    > Robosho-shellscripts
    M
    12
    > roboshop-ansible
    13
    > roboshop-ansible-roles
    14
    > shellscripts
    15
    > terraform
    16
    terraform-modules
    17
    > ec2
    18
    19
    v roboshop-ec2
    20
    .terraform
    21
    E.terraform.lock.hcl
    U
    22
    ec2.tf
    U
    23
    provider.tf
    U
    24
    25
    .gitignore
    U
    26

[^7]: EXPLORER
    . . .
    provider.tf .. \\roboshop-ec2 U X ec2.tf .. \\roboshop-ec2 U .
    provider.tf terraform-provisioners
    REPOS
    terraform-modules > roboshop-ec2 > provider.tf > ...
    > Ansible
    1
    terraform {
    N
    Concepts
    required_providers {
    3
    Ansible.MD
    M
    aws = {
    4
    source = "hashicorp/aws"
    image-1.png
    5
    version = "5.49.0" #AWS provider version, not terraform version
    image.png
    6
    {} person.json
    M
    17
    person.xml
    8
    ! person.yaml
    9
    10
    > notes
    provider "aws" {
    11
    region = "us-east-1"
    > Robosho-shellscripts
    M
    12
    > roboshop-ansible
    13
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    terraform-modules
    > ec2
    roboshop-ec2
    > .terraform
    E.terraform.lock.hcl
    U
    ec2.tf
    U
    provider.tf
    U

[^8]: EXPLORER
    . .
    provider.tf .\\roboshop-ec2 U X ec2.tf .. \\roboshop-ec2 U .
    provider.tf terraform-provisioners
    REPOS
    terraform-modules > roboshop-ec2 > provider.tf > ...
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
    5
    version = "5.49.0" #AWS provider version, not terraform version
    image.png
    6
    {} person.json
    M
    7
    person.xml
    8
    ! person.yaml
    9
    > notes
    10
    provider "aws" {
    11
    > Robosho-shellscripts
    region = "us-east-1"
    M
    12
    }
    > roboshop-ansible
    13
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    terraform-modules
    > ec2
    roboshop-ec2
    .terraform
    E.terraform.lock.hcl
    U
    ec2.tf
    U
    provider.tf
    U

[^9]: terraform-modules > @ .gitignore
    # Local . terraform directories
    N
    \*\*/ . terraform/\*
    3
    4
    # . tfstate files
    5
    \* . tfstate
    6
    \* . tfstate.\*
    7
    8
    # Crash log files
    9
    crash . log
    10
    crash. \* . log
    11
    12
    # Exclude all . tfvars files, which are likely to contain sensitive data, such as
    13
    # password, private keys, and other secrets. These should not be part of version
    14
    # control as they are data points which are potentially sensitive and subject
    15
    # to change depending on the environment.
    16
    \*. tfvars
    17
    \* . tfvars . json
    18
    19
    # Ignore override files as they are usually used to override resources locally and so
    20
    # are not checked in
    21
    override. tf
    22
    override. tf . json
    23
    \*_override. tf
    24
    \*_override. tf . json
    25
    26
    # Include override files you do wish to add to version control using negated pattern
    27
    # !example_override. tf
    28
    29
    # Include tfplan files to ignore the plan output of command: terraform plan -out=tfplan
    30
    # example: \*tfplan\*
    31
    32
    # Ignore CLI configuration files
    33
    . terraformrc
    34
    terraform. rc

[^10]: chowd@chowdary MINGW64 /e/AWSDevops/Repos (main)
    $ cd terraform-modules/
    chowd@Chowdary MINGW64 /e/AWSDevops /Repos /terraform-modules (main)
    $ cd roboshop-ec2/
    chowd@chowdary MINGW64 /e/AWSDevops /Repos/terraform-modules /roboshop-ec2 (main)
    $ terraform init
    Initializing the backend. . .
    Initializing provider plugins . . .
    Finding hashicorp/aws versions matching "5.49.0"...
    Installing hashicorp/aws v5 . 49.0. ..
    Installed hashicorp/aws v5. 49.0 (signed by Hashicorp)
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
    chowd@chowdary MINGW64 /e/AWSDevops/Repos/terraform-modules /roboshop-ec2 (main)

[^11]: chowd@Chowdary MINGW64 /e/AWSDevops/Repos/terraform-modules/roboshop-ec2 (main)
    terraform plan
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols:
    + create
    Terraform will perform the following actions:
    # module . roboshop_ec2 . aws_instance . module will be created
    resource "aws_instance" "module" {
    am7
    = "ami -Of 3c7 d07486cad139"
    arn
    = (known after apply)
    associate_public_ip_address
    = (known after apply)
    availability_zone
    = (known after apply)
    cpu_core_count
    = (known after apply)
    cpu_threads_per_core
    = (known after apply)
    disable_api_stop
    = (known after apply)
    disable_api_termination
    = (known after apply)
    ebs_optimized
    = (known after apply)
    get_password_data
    false
    host_id
    = (known after apply)
    host_resource_group_arn
    = (known after apply)
    i am_instance_profile
    (known after apply)
    id
    (known after apply)
    instance_initiated_shutdown_behavior
    (known after apply)
    instance_lifecycle
    (known after apply)
    instance_state
    (known after apply)
    instance_type
    "t2 . micro"
    ipv6_address_count
    =
    (known after apply)
    ipv6_addresses
    E
    (known after apply)
    key_name
    =
    (known after apply)
    monitoring
    (known after apply)
    outpost_arn
    =
    (known after apply)
    password_data
    = (known after apply)
    placement_group
    = (known after apply)
    placement_partition_number
    (known after apply)
    primary_network_interface_id
    =
    (known after apply)
    private_dns
    = (known after apply)
    private_ip
    = (known after apply)
    public_dns
    = (known after apply)
    public_ip
    =
    (known after apply)
    secondary_private_ips
    =
    (known after apply)
    security_groups
    = (known after apply)
    source_dest_check
    true
    spot_instance_request_id
    (known after apply)
    subnet_id
    (known after apply)
    tags_all
    = (known after apply)
    tenancy
    = (known after apply)
    user_data
    = (known after apply)
    user_data_base64
    =
    (known after apply)
    + user_data_replace_on_change
    = false
    vpc_security_group_ids
    (known after apply)
    Plan: 1 to add, 0 to change, 0 to destroy.
    Note: You didn't use the -out option to save this plan, so Terraform can't
    guarantee to take exactly these actions if you run "terraform apply" now.
    chowd@chowdary MINGW64 /e/AWSDevops /Repos/terraform-modules/roboshop-ec2 (main)

[^12]: V REPOS
    terraform-modules > roboshop-ec2 > ec2.tf > ...
    > Ansible
    1
    module "roboshop_ec2" {
    Concepts
    2
    source = " . ./ec2"
    3
    Ansible.MD
    M
    instance_type = "t3.medium"
    image-1.png
    5
    image.png
    6
    {} person.json
    M
    17
    person.xml
    8
    person.yaml
    9
    10
    notes
    11
    > Robosho-shellscripts
    M
    12
    > roboshop-ansible
    13
    > roboshop-ansible-roles
    14
    > shellscripts
    15
    > terraform
    16
    v terraform-modules
    17
    18
    > ec2
    19
    roboshop-ec2
    20
    > .terraform
    21
    E .terraform.lock.hcl
    U
    22
    ec2.tf
    U
    23
    provider.tf
    U
    24
    U
    25
    .gitignore
    26

[^13]: EXPLORER
    . . .
    hore terraform
    .gitignore terraform-multi-env
    .gitignore terraform-provisioners
    REPOS
    terraform-modules > ec2 > outputs.of > 4 output "instance_id"
    > Ansible
    output "public_ip" {
    Concepts
    2
    value = aws_instance . module. public_ip
    3
    Ansible.MD
    M
    4
    image-1.png
    15
    output "private_ip" {
    image.png
    16
    value = aws_instance . module . private_ip
    {} person.json
    M
    7
    person.xml
    8
    ! person.yaml
    9
    output "instance_id" {
    > notes
    10
    value = aws_instance . module. id
    11
    }
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    terraform-modules
    v ec2
    ec2.tf
    U
    outputs.tf
    U
    readme.MD
    U
    variables.tf
    U
    roboshop-ec2
    > .terraform
    E.terraform.lock.hcl
    U

[^14]: chowd@Chowdary MINGW64 /e/AWSDevops /Repos /terraform-modules /roboshop-ec2 (main)
    terraform plan
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols :
    create
    Terraform will perform the following actions :
    # module . roboshop_ec2 . aws_instance . module will be created
    resource "aws_instance" "module" {
    ami
    "ami-Of 3c7d07486cad139"
    arn
    (known after apply)
    associate_public_ip_address
    (known after apply)
    availability_zone
    = (known after apply)
    cpu_core_count
    = (known after apply)
    cpu_threads_per_core
    = (known after apply)
    disable_api_stop
    = (known after apply)
    disable_api_termination
    = (known after apply)
    ebs_optimized
    = (known after apply)
    get_password_data
    = false
    host_id
    (known after apply)
    host_resource_group_arn
    = (known after apply)
    i am_instance_profile
    = (known after apply)
    id
    = (known after apply)
    instance_initiated_shutdown_behavior
    = (known after apply)
    instance_lifecycle
    (known after apply)
    instance_state
    (known after
    apply)
    instance_type
    "t3 . medium"
    ipv6_address_count
    = (known after apply)
    ipv6_addresses
    = (known after apply)
    key_name
    = (known after apply)
    monitoring
    = (known after apply)
    outpost_arn
    (known after apply)
    password_data
    = (known after apply)
    placement_group
    = (known after apply)
    placement_partition_number
    = (known after apply)
    primary_network_interface_id
    = (known after apply)
    private_dns
    (known after apply)
    private_ip
    = (known after apply)
    public_dns
    = (known after apply)
    public_ip
    = (known after apply)
    secondary_private_ips
    = (known after apply)
    security_groups
    = (known after apply)
    source_dest_check
    = true
    spot_instance_request_id
    = (known after apply)
    subnet_id
    = (known after apply)
    tags_al1
    = (known after apply)
    tenancy
    = (known after apply)
    + user_data
    (known after apply)
    user_data_base64
    = (known after apply)
    + user_data_replace_on_change
    = false
    vpc_security_group_ids
    (known after apply)
    Plan: 1 to add, 0 to change, 0 to destroy.
    Note: You didn't use the -out option to save this plan, so Terraform can't
    guarantee to take exactly these actions if you run "terraform apply"
    now.

[^15]: REPOS
    terraform-modules > roboshop-ec2 > variables.of > < variable "tagssssss"
    > Ansible
    1
    variable "instance_typeeeeee" {
    Concepts
    2
    default = "t3.medium"
    3
    Ansible.MD
    M
    14
    image-1.png
    5
    variable "tagssssss" {
    image.png
    16
    default = {
    {} person.json
    M
    7
    Name = "roboshop"
    person.xml
    18
    terraform = "true"
    person.yaml
    9
    environment = "dev"
    10
    notes
    11
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    v terraform-modules
    v ec2
    ec2.tf
    U
    variables.tf
    U
    roboshop-ec2
    > .terraform
    E .terraform.lock.hcl
    U
    ec2.tf
    U
    provider.tf
    U
    variables.tf
    U

[^16]: V REPOS
    terraform-modules > roboshop-ec2 > ec2.tf > ...
    > Ansible
    H
    module "roboshop_ec2" {
    Concepts
    2
    source = " . ./ec2"
    3
    Ansible.MD
    M
    instance_type = var . instance_typeeeeee
    14
    tags = var . tagssssss
    image-1.png
    15
    image.png
    16
    {} person.json
    M
    7
    person.xml
    8
    ! person.yaml
    9
    > notes
    10
    11
    > Robosho-shellscripts
    M
    12
    > roboshop-ansible
    13
    > roboshop-ansible-roles
    14
    > shellscripts
    15
    > terraform
    16
    v terraform-modules
    17
    18
    v ec2
    O
    19
    ec2.tf
    U
    20
    variables.tf
    U
    21
    roboshop-ec2
    22
    > .terraform
    23
    E .terraform.lock.hcl
    U
    24
    ec2.tf
    U
    25
    26

[^17]: chowd@Chowdary MINGW64 /e/AWSDevops/Repos/terraform-modules /roboshop-ec2 (main)
    $ terraform plan
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols:
    create
    Terraform will perform the following actions :
    # module . roboshop_ec2. aws_instance . module will be created
    resource "aws_instance" "module" {
    ami
    "ami -Of 3c7 d07486cad139"
    arn
    = (known after apply)
    associate_public_ip_address
    (known after apply)
    availability_zone
    (known after apply)
    cpu_core_count
    (known after apply)
    cpu_threads_per_core
    (known after apply)
    disable_api_stop
    (known after apply)
    disable_api_termination
    =
    (known after apply)
    ebs_optimized
    (known after apply)
    get_password_data
    = false
    host_id
    (known after apply)
    host_resource_group_arn
    (known after apply)
    1 am_instance_profile
    =
    (known after apply)
    id
    (known after apply)
    instance_initiated_shutdown_behavior
    E
    (known after apply)
    instance_lifecycle
    (known after apply)
    instance_state
    (known after apply)
    instance_type
    "t3. medium"
    ipv6_address_count
    (known after apply)
    ipv6_addresses
    (known after apply)
    key_name
    (known after apply)
    monitoring
    (known after apply)
    outpost_arn
    (known after apply)
    password_data
    E
    (known after apply)
    placement_group
    (known after apply)
    placement_partition_number
    (known after apply)
    primary_network_interface_id
    (known after
    apply)
    private_dns
    (known after apply)
    private_ip
    (known after apply)
    public_dns
    =
    (known after apply)
    public_ip
    =
    (known after apply)
    secondary_private_ips
    E
    (known after apply)
    security_groups
    (known after apply)
    source_dest_check
    true
    spot_instance_request_id
    (known after apply)
    subnet_id
    (known after apply)
    +
    tags
    "Name"
    E
    "roboshop"
    "environment"
    =
    "dev"
    "terraform"
    = "true"
    }
    tags_al1
    "Name"
    "roboshop"
    "environment"
    =
    "dev"
    "terraform'
    = "true"
    tenancy
    = (known after apply)
    +
    user_data
    (known after apply)
    user_data_base64
    (known after apply)
    +
    user_data_replace_on_change
    = false
    vpc_security_group_ids
    (known after apply)
    Plan: 1 to add, 0 to change, 0 to destroy.

[^18]: REPOS
    terraform-modules > roboshop-ec2 > outputs.of > < output "private"
    > Ansible
    1
    output "public" {
    N
    Concepts
    value = module . roboshop_ec2. public_ip
    3
    Ansible.MD
    M
    4
    image-1.png
    5
    output "private" {
    image.png
    6
    value = module . roboshop_ec2 . private_ip
    {} person.json
    M
    7
    person.xml
    ! person.yaml
    > notes
    O
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    > terraform
    v terraform-modules
    > ec2
    v roboshop-ec2
    > .terraform
    E.terraform.lock.hcl
    U
    ec2.tf
    U
    outputs.tf
    U
    provider.tf
    U
    variables.tf
    U
    .gitignore
    U

[^19]: source_dest_check
    =
    true
    spot_instance_request_id
    E
    (known after apply)
    +
    subnet_id
    (known after apply)
    +
    tags
    +
    "Name"
    "roboshop"
    +
    "environment"
    E
    "dev"
    +
    "terraform"
    =
    "true"
    +
    tags_a17
    "Name"
    "roboshop"
    +
    "environment"
    E
    "dev"
    +
    "terraform"
    "true"
    +
    tenancy
    = (known after apply)
    +
    user_data
    E
    (known after apply)
    user_data_base64
    = (known after apply)
    +
    user_data_replace_on_change
    E
    false
    +
    vpc_security_group_ids
    E
    (known after apply)
    Plan: 1 to add, 0 to change, 0 to destroy.
    Changes to Outputs :
    + private = (known after apply)
    public = (known after apply)
    Note: You didn't use the -out option to save this plan, so Terraform can't
    guarantee to take exactly these actions if you run "terraform apply" now.
    chowd@chowdary MINGW64 /e/AWSDevops /Repos /terraform-modules /roboshop-ec2 (main)

[^20]: subnet_id
    (known after apply)
    tags
    "Name"
    E
    "roboshop"
    +
    "environment"
    "dev"
    +
    "terraform"
    "true"
    +
    tags_al1
    =
    "Name"
    "roboshop"
    "environment"
    "dev"
    +
    "terraform"
    =
    "true"
    }
    tenancy
    =
    (known after apply)
    user_data
    =
    (known after apply)
    user_data_base64
    =
    (known after apply)
    user_data_replace_on_change
    = false
    vpc_security_group_ids
    (known after apply)
    Plan: 1 to add, 0 to change, 0 to destroy.
    Changes to Outputs:
    private = (known after apply)
    + public = (known after apply)
    module . roboshop_ec2 . aws_instance . module: Creating. . .
    module . roboshop_ec2 . aws_instance . module: Stil1 creating. .. \[10s elapsed\]
    module . roboshop_ec2 . aws_instance . module: Creation complete after 17s \[id=i-0c4d007c3e250804f\]
    Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
    Outputs :
    private = "172. 31.40.74"
    public = "35 . 174. 10.83"
    chowd@Chowdary MINGW64 /e/AWSDevops/Repos /terraform-modules /roboshop-ec2 (main)
    $

[^21]: subnet_id
    (known after apply)
    tags
    "Name"
    E
    "roboshop"
    +
    "environment"
    "dev"
    +
    "terraform"
    "true"
    +
    tags_al1
    =
    "Name"
    "roboshop"
    "environment"
    "dev"
    +
    "terraform"
    =
    "true"
    }
    tenancy
    =
    (known after apply)
    user_data
    =
    (known after apply)
    user_data_base64
    =
    (known after apply)
    user_data_replace_on_change
    = false
    vpc_security_group_ids
    (known after apply)
    Plan: 1 to add, 0 to change, 0 to destroy.
    Changes to Outputs:
    private = (known after apply)
    + public = (known after apply)
    module . roboshop_ec2 . aws_instance . module: Creating. . .
    module . roboshop_ec2 . aws_instance . module: Stil1 creating. .. \[10s elapsed\]
    module . roboshop_ec2 . aws_instance . module: Creation complete after 17s \[id=i-0c4d007c3e250804f\]
    Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
    Outputs :
    private = "172. 31.40.74"
    public = "35 . 174. 10.83"
    chowd@Chowdary MINGW64 /e/AWSDevops/Repos /terraform-modules /roboshop-ec2 (main)
    $

[^22]: aws
    Search
    (?)
    Services
    Q
    \[Alt+S\]
    A
    N. Virginia
    chowda
    EC2
    Route 53
    OF IAM
    CO VPC
    $3
    DynamoDB
    Instances (1/1) Info
    Connect
    Instance state
    Actions
    Launch instances
    4
    EC2 Dashboard
    X
    1
    EC2 Global View
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    <
    Events
    Name _
    Instance ID
    Instance state
    Instance type
    Status check
    Alarm status
    Availability
    Console-to-Code Preview
    roboshop
    i-0c4d007c3e250804f
    Running
    Q Q
    t3.medium
    Initializing
    View alarms +
    us-east-1a
    Instances

[^23]: Plan: 0 to add, 0 to change, 1 to destroy.
    Changes to Outputs:
    private = "172. 31. 40.74" -> null
    - public = "35 . 174. 10.83" -> null
    module . roboshop_ec2 . aws_instance . module: Destroying. .. \[id=i-0c4d007c3e250804f\]
    module . roboshop_ec2. aws_instance . module: Still destroying... \[id=i-0c4d007c3e250804f, 10s elapsed\]
    module . roboshop_ec2. aws_instance . module: Still destroying. . .
    \[id=i-0c4d007 c3e250804f, 20s elapsed\]
    module . roboshop_ec2. aws_instance . module: Still destroying. .
    \[id=i-0c4d007c3e250804f , 30s elapsed\]
    module . roboshop_ec2 . aws_instance . module: Still destroying. . .
    \[id=i-0c4d007c3e250804f, 40s elapsed\]

[^24]: physical space
    AC
    power backup
    network connections
    security gaurds
    network field engineer
    linux admin team

[^25]: Village --> VPC
    - -- -------------
    streets --> admin, proper organisation and maintaince
    I
    subnets -->
    HR department
    Databases
    Fianance

[^26]: Roads
    Public Affairs
    Ministers
    PMO
    Secure roads
    private roads
    Arch
    X
    private roads
    Secure roads
    Public Affairs
    Ministers
    PMO
    Roads

[^27]: Public Subnets
    Private Subnets
    Database Servers
    Public Subnets
    Private Subnets
    Database Servers

[^28]: 15. 197 .142.173 --> facebook IP
    home network --> facebook network --> particular server
    IP = Network + Server IP

[^29]: 2 to the Power of 32 is equal to 4294967296.

[^30]: 10.0.0.0/16 --> first 16 bits are for network, next 16 bits are for servers
    10 .0.0.1
    10 .0.0.2
    10 .0.0.3
    10 .0.0.3
    = 212
    0
    0
    1
    0
    1
    - = 213
    0
    0 0
    10
    OH
    10
    01 1
    I
    0 0
    1
    0
    1
    O
    111

