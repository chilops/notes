---
title: 25Day_Terraform
uuid: 0cc27282-10e5-11ef-8a05-2e40d90dfe07
version: 725
created: '2024-05-13T10:25:41+05:30'
tags:
  - terraform
---

*<mark style="background-color:#f8d616;">**Topics:**<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8d616;">Ansible, shell advantages & disadvantages<!-- {"backgroundCycleColor":"25"} --></mark>* 

1. *<mark style="background-color:#f8d616;">Terraform intro<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8d616;">Terraform setup along with AWS CLI<!-- {"backgroundCycleColor":"25"} --></mark>*

1. *<mark style="background-color:#f8d616;">Let us create one EC2 instance using terraform<!-- {"backgroundCycleColor":"25"} --></mark>*

\

\

*<mark style="background-color:#f8914d;">**Ansible, shell advantages & disadvantages**<!-- {"backgroundCycleColor":"24"} --></mark>* 

*Ansible - Its a configuration management (configuration as a code)*

*<mark style="background-color:#fff;">Manual configuration -<!-- {"backgroundCycleColor":"11"} --></mark> Disadvantages in manual - Time taking, Human errors*

*shell scripting,* 

*Ansible(ansible preffered for big/large environments)*

\

\

\

\

*<mark style="background-color:#f8914d;">**Terraform intro** -<!-- {"backgroundCycleColor":"24"} --></mark> <mark style="background-color:#fff;">Its popular for Infrastructure as code<!-- {"backgroundCycleColor":"11"} --></mark>* 

\

*Consistent Infrastructure - In both Dev, production we can use same code*  

*<mark style="background-color:#f8d616;">Terraform<!-- {"backgroundCycleColor":"25"} --></mark> - same code will with all environments(DEV,QA,TESTING,PRODUCTION), So infrastructure is consistent across all environment's* 

*Automated infra -- > CRUD*

*create*

*read*

*update*

*delete*

\

*<mark style="background-color:#f3de6c;">**Terraform purpose**<!-- {"backgroundCycleColor":"14"} --></mark>*

- *It's a Inventory management*

- *cost optimization --  Create when required, stop or delete when not required*

- *Automatic dependent management -- We can create resources, Terraform will take care of dependency management(EX. Route53 creation is dependent on EC2 instances)*

- *Terraform Modules -- You can create terraform code as modules, Once you write the code for project1 then you don't need to write code for project2 and we can use it without writing from scratch.*

- *Declarative way of creative infrastructure -- what is Declarative? whatever you write you will get it, If you write correct syntax.* 

    - *Easy syntax , No need to follow sequence.*

- *If you use terraform restoring the project to original state will be quick and easy.*

- *Terraform is a hybrid cloud - AWS, GCP, Azure cloud etc* 

*Terraform providers*

![63385f94-5b5e-4555-8d5f-467e2e8960ff.png|897.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/63385f94-5b5e-4555-8d5f-467e2e8960ff.png) [^1]

![a4e49207-da3c-4726-99a1-73f1eea8aea1.png|876](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/a4e49207-da3c-4726-99a1-73f1eea8aea1.png) [^2]

\

*<mark style="background-color:#f3de6c;">version control<!-- {"backgroundCycleColor":"14"} --></mark>*

*If you keep code in Git, we can maintain history and you can get back previous versions*

\

\

\

*<mark style="background-color:#f8914d;">**Terraform setup along with AWS CLI**<!-- {"backgroundCycleColor":"24"} --></mark>*

1. *Download terraform*

1. *Installing AWS CLI*

\

![6b072c51-2fec-417a-859e-be5a9aa68659.png|891.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/6b072c51-2fec-417a-859e-be5a9aa68659.png) [^3]

\

![878c547e-31ec-4d82-9ce8-59392d769170.png|883.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/878c547e-31ec-4d82-9ce8-59392d769170.png) [^4]

![e46d64f0-a8e8-4b91-a910-726f6830963a.png|886.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/e46d64f0-a8e8-4b91-a910-726f6830963a.png) [^5]

\

*Now search for environment variable in windows.*

![3e484084-3173-4b50-a3de-3e4e98434c63.png|515.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/3e484084-3173-4b50-a3de-3e4e98434c63.png) [^6]

![89bb8b9b-31a0-4add-a5c2-1704bd0124ae.png|613.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/89bb8b9b-31a0-4add-a5c2-1704bd0124ae.png) [^7]

\

*System variables - it will allow all users -- so give under path - create new E:\\Softwares*

![d78a24a8-b9bd-45af-b6ec-3c812c86f3ea.png|799.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/d78a24a8-b9bd-45af-b6ec-3c812c86f3ea.png) [^8]

\

*Now open cmd(run as admin) enter the terraform command then it will show below output.*

```
terraform
```

![ab07d27b-b83f-4bcb-80c2-94af8d092782.png|554](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/ab07d27b-b83f-4bcb-80c2-94af8d092782.png) [^9]

\

```
terraform version
```

![eabf9447-1f3c-4206-adf4-2361038dcb46.png|438](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/eabf9447-1f3c-4206-adf4-2361038dcb46.png) [^10]

\

*<mark style="background-color:#f3de6c;">**Now download AWS CLI in windows its needed to communicate to aws account**<!-- {"backgroundCycleColor":"14"} --></mark>*

\

![eae1ef7e-e38e-43a1-8419-5c866e3ca219.png|724.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/eae1ef7e-e38e-43a1-8419-5c866e3ca219.png) [^11]

![28fb2628-7ee6-4769-8a50-366d79f60613.png|452](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/28fb2628-7ee6-4769-8a50-366d79f60613.png) [^12]

*Installing*

![66bab4aa-bb93-4c8e-85a9-3d0a052d61bb.png|412](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/66bab4aa-bb93-4c8e-85a9-3d0a052d61bb.png) [^13]

![d3932d4c-b3c5-405a-abe2-f9e0adbbb945.png|456](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/d3932d4c-b3c5-405a-abe2-f9e0adbbb945.png) [^14]

\

![92c943f4-867c-40fb-b582-b67216cdf1f2.png|646](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/92c943f4-867c-40fb-b582-b67216cdf1f2.png) [^15]

*To check AWS version*

```
aws --version
```

![973fb4fe-f139-40e4-8cac-05901c44c9f4.png|605](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/973fb4fe-f139-40e4-8cac-05901c44c9f4.png) [^16]

\

\

\

*Creating a terraform repo/folder:*

![41453e7e-0ef9-4436-88ad-9e4ab3054779.png|353](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/41453e7e-0ef9-4436-88ad-9e4ab3054779.png) [^17]

\

*Creating a new terraform repository in GITHUB*

![5ebbfb7e-5cb0-4826-aefa-fcb2a1f527ff.png|601.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/5ebbfb7e-5cb0-4826-aefa-fcb2a1f527ff.png) [^18]

\

\

```
cd /e/awsdevops/Repos/
pwd
cd terraform/
git init
git remote add origin git@github.com:chilops/terraform.git
```

![5c78fc29-713b-44be-aeed-7c4b932b1c45.png|728](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/5c78fc29-713b-44be-aeed-7c4b932b1c45.png) [^19]

\

*creating session1 folder*

![67923caa-3a3c-4b09-8237-acf25c29bfcf.png|328](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/67923caa-3a3c-4b09-8237-acf25c29bfcf.png) [^20]

\

*<mark style="background-color:#f8914d;">**Let us create one EC2 instance using terraform:**<!-- {"backgroundCycleColor":"24"} --></mark>*

\

***HCL** -- > Hashicorp configuration language*

*Variables*

*conditions*

*datatypes*

*loops*

*functions*

\

*<mark style="background-color:#f8d616;">**Syntax:**<!-- {"backgroundCycleColor":"25"} --></mark>*

*resource "what-resource" "name-your-resource-your-wish" {*

\

*}*

\

\

*<mark style="background-color:#f8d616;">**Creating a EC2 folder under session1**<!-- {"backgroundCycleColor":"25"} --></mark>*

*1. create IAM admin user*

*2. create access key and secret key*

*3. AWS configure*

\

![d312b6ab-200d-4251-933c-9778f8567add.png|324](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/d312b6ab-200d-4251-933c-9778f8567add.png) [^21]

\

***Now Terraform requires <mark style="background-color:#f8d616;">AWS provider configuration<!-- {"backgroundCycleColor":"25"} --></mark> - To create AWS infra***

\

***.tf** -- extension for terraform* 

\

![60965168-e520-4bef-9c81-0806b5313d2c.png|943.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/60965168-e520-4bef-9c81-0806b5313d2c.png) [^22]

\

```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.49.0"  #AWS provider version, not terraform version
    }
  }
}

provider "aws" {
     region = "us-east-1"
}
```

\

![6f29deac-7957-4672-b339-23bd55e577c6.png|873.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/6f29deac-7957-4672-b339-23bd55e577c6.png) [^23]

\

*Now we need to create one user in AWS -IAM*

\

![c8575e1b-272f-40c8-b585-6f6ad830d492.png|837.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/c8575e1b-272f-40c8-b585-6f6ad830d492.png) [^24]

![54f21e4a-00bd-47b6-91b6-c8ba01eccbcb.png|843.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/54f21e4a-00bd-47b6-91b6-c8ba01eccbcb.png) [^25]

![8f200aa7-0dff-438a-bc2d-e8a5362a9745.png|842.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/8f200aa7-0dff-438a-bc2d-e8a5362a9745.png) [^26]

![1f4f3b39-1cf0-4327-8ee1-60ded3edb479.png|849.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/1f4f3b39-1cf0-4327-8ee1-60ded3edb479.png) [^27]

![cf9b6efb-3127-4de2-b07f-e3092f33c06a.png|845.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/cf9b6efb-3127-4de2-b07f-e3092f33c06a.png) [^28]

\

*Copy both access key & secret keys and save it secret*

![d7227f2a-87c2-4ff1-b86b-b4dd814ed0b8.png|879.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/d7227f2a-87c2-4ff1-b86b-b4dd814ed0b8.png) [^29]

\

![b166a805-d5f4-4566-b4c1-8c6f05aa792c.png|887.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/b166a805-d5f4-4566-b4c1-8c6f05aa792c.png) [^30]

\

*Now AWS cli can access our AWS account using AWS CLI*

![73300346-cb68-47d3-a04b-8fc582043c2e.png|814](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/73300346-cb68-47d3-a04b-8fc582043c2e.png) [^31]

\

*AWS access & secret will save in below folder in our laptop/server.*

![957fbfa7-0c66-4369-ab23-6c7a6e2ec3c7.png|861.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/957fbfa7-0c66-4369-ab23-6c7a6e2ec3c7.png) [^32]

\

*To get Devops-practice AWS - **AMI ID***

![b6558db6-ca9f-4b1a-a483-1a46277dd364.png|942.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/b6558db6-ca9f-4b1a-a483-1a46277dd364.png) [^33]

\

\

\

\

\

\

*where to run terraform command, wherever <mark style="background-color:#f8914d;">**.tf file**<!-- {"backgroundCycleColor":"24"} --></mark> exists you have to run terraform command in that directory*

```
cd .\terraform\
cd .\session1\
cd .\EC2\
ls
```

![207d666c-0044-4020-9ba4-89d69ca8fa3c.png|587](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/207d666c-0044-4020-9ba4-89d69ca8fa3c.png) [^34]

\

![a5263f4a-b837-46a6-988c-bd2e98cf2f19.png|589](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/a5263f4a-b837-46a6-988c-bd2e98cf2f19.png) [^35]

\

*provider.tf*

```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.49.0"  #AWS provider version, not terraform version
    }
  }
}

provider "aws" {
     region = "us-east-1"
}
```

\

![b9d7d0d2-f173-4f3d-94a9-51531ab7fbf6.png|815.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/b9d7d0d2-f173-4f3d-94a9-51531ab7fbf6.png) [^36]

\

***commands***

```
terraform init    -- It initialize the provider
```

![2da7c3ac-d5eb-4a49-b19d-56b807a5d611.png|747](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/2da7c3ac-d5eb-4a49-b19d-56b807a5d611.png) [^37]

*or*

![7bf6bcef-54a0-4f55-9a9a-178f88c64faf.png|735](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/7bf6bcef-54a0-4f55-9a9a-178f88c64faf.png) [^38]

\

*.terraform folder is created and provider downloaded (but in my case folder is not created)*

![](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/e29d38d8-3ec6-4717-a305-ffb261dcb4b8.png) [^39]

\

*-- Just a plan, will not create actually*

```
terraform plan     
```

![b7af8f46-ffdf-47de-be90-feaad9bf3338.png|654](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/b7af8f46-ffdf-47de-be90-feaad9bf3338.png) [^40]

\

*-- It will apply the changes & create a resource*

```
terraform apply
```

\

![ea56d75b-ac27-4847-8e75-91e65fd0e51d.png|801](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/ea56d75b-ac27-4847-8e75-91e65fd0e51d.png) [^41]

\

*Instance created:*

![c702fe75-9bc0-4737-8dd8-929cb01a512b.png|847.3333740234375](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/c702fe75-9bc0-4737-8dd8-929cb01a512b.png) [^42]

\

*-- To destroy all infra or web instance*

```
terraform destroy
```

![6c4f2767-ecbb-4209-88f6-93bbee608a1f.png|847](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/6c4f2767-ecbb-4209-88f6-93bbee608a1f.png) [^43]

![d196a081-5c8e-4930-9922-8462104d1d91.png|846](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/d196a081-5c8e-4930-9922-8462104d1d91.png) [^44]

\

Instance destroyed now

![4c607726-2547-417a-b320-fab7f62e4e8b.png|958](https://images.amplenote.com/0cc27282-10e5-11ef-8a05-2e40d90dfe07/4c607726-2547-417a-b320-fab7f62e4e8b.png) [^45]

\

1\.00

[^1]: C registry.terraform.io/browse/providers
    Terraform
    Registry
    Search all resources
    Browse
    Publish v Sign-in
    Use Terraform Cloud for free 7
    Providers
    Modules
    O Policy Libraries
    Run Tasks
    Filters
    Clear Filters
    @ Providers
    Tier
    Providers are a logical abstraction of an upstream API. They are responsible for understanding API interactions and exposing resources.
    Official
    Partner
    Community
    aws
    Category
    A
    OHashiCorp Platform
    O Infrastructure Management
    AWS
    Azure
    Google Cloud Platform
    Public Cloud
    Asset Management
    Cloud Automation
    Communication & Messaging
    Container Orchestration
    Continuous Integration/Deployment (CI/CD)
    Data Management
    Kubernetes
    Alibaba Cloud
    Oracle Cloud
    Database
    Infrastructure

[^2]: HTTP
    Local
    N
    Nomad
    by: hashicorp
    by: hashicorp
    by: hashicorp
    O
    Null
    Oracle Public Cloud
    Oracle Cloud Platform
    ORACLE
    ORACLE
    by: hashicorp
    by: hashicorp
    by: hashicorp
    O
    Random
    Salesforce
    Template
    by. hashicorp
    by: hashicorp
    by: hashicorp
    Terraform Cloud
    Time
    TLS
    by: hashicorp
    by: hashicorp
    by: hashicorp
    Vault
    VMware vSphere
    Waypoint
    vmware
    by: hashicorp
    by: hashicorp
    by: hashicorp

[^3]: C
    @ https://developer.hashicorp.com/terraform/install
    Downloads
    Terraform
    Install
    Tutorials Documentation \\ Registry C Try Cloud
    terraform_1.
    brew tap hashicorp/tap
    3.6 MB/s - 21.8
    < Terraform Home
    brew install hashicorp/tap/terraform
    See more
    Install Terraform
    Binary download
    Operating Systems
    AMD64
    ARM64
    Download
    Download
    Version: 1.8.3
    Version: 1.8.3
    macOS
    Windows
    Linux
    Windows
    FreeBSD
    Binary download
    OpenBSD
    Solaris
    386
    AMD64
    Download
    Download
    Version: 1.8.3
    Version: 1.8.3
    Release information

[^4]: C
    >
    Downloads > terraform_1.8.3_windows_amd64
    +
    New v
    CO
    (A
    N Sort
    View
    . .
    Home
    Name
    Date modified
    Type
    Size
    Gallery
    Today
    OneDrive - Personal
    LICENSE.txt
    13-05-2024 11:42
    Text Document
    5 KB
    Apps
    terraform.exe
    13-05-2024 11:42
    Application
    88,072 KB
    Deskton

[^5]: Softwares
    X
    +
    C
    >
    This PC > Professional (E:) > Softwares
    >
    +
    New v
    N Sort
    =View
    . . .
    Home
    Name
    Date modified
    Type
    Size
    Gallery
    Amplenote Desktop Setup 0.4.4.exe
    04-05-2024 14:45
    Application
    81,699 KB
    OneDrive - Personal
    free_screen_recorder.zip
    26-11-2023 08:34
    Compressed (zipped)...
    15,972 KB
    Apps
    D2 putty-64bit-0.79-installer.msi
    02-12-2023 12:13
    Windows Installer Pa..
    3,622 KB
    Desktop
    SuperPuttySetup-1.4.0.9.msi
    02-12-2023 12:49
    Windows Installer Pa...
    1,832 KB
    Documents
    terraform.exe
    13-05-2024 11:42
    Application
    88,072 KB
    Pictures

[^6]: Q envil
    All
    Apps
    Documents
    Web
    Settings
    Folders
    Ph
    416 8
    . . .
    Best match
    Edit the system environment
    variables
    Control panel
    Edit the system environment variables
    Settings
    Control panel
    Edit environment variables for
    >
    your account
    Open
    Change brightness automatically

[^7]: System Properties
    X
    Type
    Size
    Computer Name Hardware Advanced System Protection Remote
    Environment Variables
    You must be logged on as an Administrator to make most of these changes.
    User variables for chowd
    Performance
    Visual effects, processor scheduling, memory usage, and virtual memory
    Variable
    Value
    OneDrive
    C:\\Users\\chowd\\OneDrive
    Settings...
    Path
    C:\\Users\\chowd\\AppData\\Local\\Microsoft\\ WindowsApps;C:\\Use...
    TEMP
    C:\\Users\\chowd\\AppData\\Local\\ Temp
    User Profiles
    TMP
    C:\\Users\\chowd\\AppData\\Local\\ Temp
    Desktop settings related to your sign-in
    Settings..
    Startup and Recovery
    System startup, system failure, and debugging information
    New...
    Edit...
    Delete
    Settings..
    System variables
    Environment Variables...
    Variable
    Value
    ComSpec
    C:\\Windows\\system32\\cmd.exe
    DriverData
    C:\\Windows\\System32\\ Drivers\\ DriverData
    OK
    Cancel
    Apply
    NUMBER_OF_PROCESSORS
    12
    OS
    Windows_NT
    Path
    C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbe...
    PATHEXT
    .COM;EXE; BAT;.CMD; VBS; VBE;JS;JSE;.WSF;.WSH;.MSC
    PROCESSOR_ARCHITECTURE AMD64
    PROCESSOR IDENTIFIFR
    Intel64 Family 6 Model 154 Stenning 4. GenuineIntel
    New...
    Edit...
    Delete
    0:34 / 1:42.27
    Q Search
    OK
    Cancel

[^8]: System Properties
    X
    Type
    Size
    Edit environment variable
    X
    Computer Name Hardware Advanced System Protection Remote
    Environment Variables
    You must be logged on as an Administrator to make most of these changes.
    %SystemRoot% \\system32
    New
    User variables for chowd
    Performance
    %SystemRoot%
    Visual effects, processor scheduling, memory usage, and virtual memory
    Variable
    Value
    %SystemRoot%\\System32\\Wbem
    Edit
    OneDrive
    C:\\Users\\cho
    %SYSTEMROOT%\\System32\\WindowsPowerShell\\v1.0\\
    Settings...
    Path
    C:\\Users\\cho
    %SYSTEMROOT%\\System32\\OpenSSH\\
    Browse...
    TEMP
    C:\\Users\\cho
    C:\\Program Files\\dotnet\\
    User Profiles
    TMP
    C:\\Users\\cho
    C:\\Program Files\\PUTTY
    Desktop settings related to your sign-in
    C:\\Program Files\\Git\\cmd
    Delete
    E:\\Softwares
    Settings..
    Move Up
    Startup and Recovery
    System startup, system failure, and debugging information
    Move Down
    Settings...
    System variables
    Edit text...
    Environment Variables...
    Variable
    Value
    ComSpec
    C:\\Windows
    DriverData
    C:\\Windows\\
    OK
    Cancel
    Apply
    NUMBER_OF_PROCESSORS
    12
    OS
    Windows_NT
    Path
    C:\\Windows\\
    PATHEXT
    .COM; EXE;.B.
    PROCESSOR_ARCHITECTURE AMD64
    PROCESSOR IDENTIFIFR
    Intel64 Family
    OK
    Cancel

[^9]: 0:. Administrator: Command Prompt
    licrosoft Windows \[Version 10.0.22631.3527\]
    c) Microsoft Corporation. All rights reserved.
    : \\Windows \\System32>terraform -
    sage: terraform \[global options\] <subcommand> \[args \]
    he available commands for execution are listed below.
    he primary workflow commands are given first, followed by
    ess common or more advanced commands.
    lain commands :
    init
    Prepare your working directory for other commands
    validate
    Check whether the configuration is valid
    plan
    Show changes required by the current configuration
    apply
    Create or update infrastructure
    destroy
    Destroy previously-created infrastructure
    11 other commands :
    console
    Try Terraform expressions at an interactive command prompt
    fmt
    Reformat your configuration in the standard style
    force-unlock
    Release a stuck lock on the current workspace
    get
    Install or upgrade remote Terraform modules
    graph
    Generate a Graphviz graph of the steps in an operation
    import
    Associate existing infrastructure with a Terraform resource
    login
    Obtain and save credentials for a remote host
    logout
    Remove locally-stored credentials for a remote host
    metadata
    Metadata related commands
    output
    Show output values from your root module
    providers
    Show the providers required for this configuration

[^10]: C: \\Users\\chowd>terraform version
    Terraform v1.8.3
    on windows_amd64
    C: \\Users\\chowd>

[^11]: G
    https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
    . ..
    aws
    Q Search in this guide
    Contact Us
    English
    Return to the Console
    AWS >
    Documentation
    AWS Command Line Interface
    > User Guide for Version 2
    Feedback \[\] Preferences (@)
    AWS Command Line
    X
    AWS CLI install and update instructions
    On this page
    X
    Interface
    User Guide for Version 2
    For installation instructions, expand the section for your operating system.
    AWS CLI install and update
    instructions
    About the AWS CLI
    Linux
    Troubleshooting AWS CLI install
    Get started
    and uninstall errors
    Prerequisites
    Next steps
    Install/Update
    macOS
    Past releases
    Build and install from source
    Amazon ECR Public/Docker
    Windows
    Setup
    Configure the AWS CLI
    Authentication and access
    Install and update requirements
    credentials
    . We support the AWS CLI on Microsoft-supported versions of 64-bit Windows.
    Use the AWS CLI
    . Admin rights to install software
    D Code examples
    Security
    Install or update the AWS CLI
    Troubleshoot errors
    To update your current installation of AWS CLI on Windows, download a new installer each
    D Migration guide
    time you update to overwrite previous versions. AWS CLI is updated regularly. To see when the
    Uninstall
    latest version was released, see the AWS CLI version 2 Changelog on GitHub.
    Introducing Amazon Q
    X
    Receive guidance, get troubleshooting tips,
    Document History
    1. Download and run the AWS CLI MSI installer for Windows (64-bit):
    and learn about AWS services and
    AWS Glossary
    https://awscli.amazonaws.com/AWSCLIV2.msi\[
    capabilities.
    Alternatively, you can run the msiexec command to run the MSI installer.

[^12]: Downloads
    Do ...
    Cons
    AWSCLIV2.msi
    Open file
    eferen
    terraform_1.8.3_windows_amd64.zip
    Open file
    See more
    AWS CLI install and update

[^13]: AWS Command Line Interface v2 Setup
    X
    aws
    Welcome to the AWS Command Line
    Interface v2 Setup Wizard
    The Setup Wizard will install AWS Command Line Interface v2
    on your computer. Click Next to continue or Cancel to exit the
    Setup Wizard.
    Back
    Next
    Cancel

[^14]: AWS Command Line Interface vz Setup
    Installing AWS Command Line Interface v2
    aws
    Please wait while the Setup Wizard installs AWS Command Line Interface v2.
    Status:
    Copying new files File: \[1\], Directory: \[9\], Size: \[6\]
    Back
    Next
    Cancel

[^15]: terraform.exe
    AWS Account
    Interface

[^16]: Command Prompt
    X
    +
    Microsoft Windows \[Version 10. 0.22631.3527\]
    (c) Microsoft Corporation. All rights reserved.
    C: \\Users\\chowd>aws --version
    aws-cli/2. 15. 48 Python/3.11.8 Windows/10 exe/AMD64 prompt/ off
    C: \\Users\\chowd>

[^17]: XI
    File Edit Selection View Go Run
    Term
    EXPLORER
    ... \\n
    3
    REPOS
    > Ansible
    > Concepts
    > notes
    6
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    terraform

[^18]: C
    https://github.com/new
    E
    New repository
    Q Type to search
    Create a new repository
    A repository contains all project files, including the revision history. Already have a project repository elsewhere?
    Import a repository.
    Required fields are marked with an asterisk (\*).
    Owner \*
    Repository name \*
    chilops
    terraform
    terraform is available.
    Great repository names are short and memorable. Need inspiration? How about reimagined-garbanzo ?
    Description (optional)
    O
    Public
    Anyone on the internet can see this repository. You choose who can commit.
    o e
    Private
    You choose who can see and commit to this repository.
    Initialize this repository with:
    Add a README file
    This is where you can write a long description for your project. Learn more about READMEs.

[^19]: chowd@chowdary MINGW64
    $ cd /e/aws devops /Repos /
    chowd@chowdary MINGW64 /e/awsdevops /Repos (main)
    $ pwd
    /e/aws devops /Repos
    chowd@Chowdary MINGW64 /e/awsdevops /Repos (main)
    $ cd terraform/
    chowd@chowdary MINGW64 /e/awsdevops/Repos/terraform (main)
    $ git init
    Initialized empty Git repository in E: /AWSDevops/Repos/terraform/.git/
    chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform (main)
    $ git remote add origin git@github . com: chilops/terraform.git
    chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform (main)

[^20]: EXPLORER
    . . .
    .. \\mong
    V REPOS
    Robo
    > Ansible
    44
    > Concepts
    45
    > notes
    46
    > Robosho-shellscripts
    47
    M
    48
    > roboshop-ansible
    49
    > roboshop-ansible-roles
    50
    > shellscripts
    51
    v terraform \\ session1 -
    52
    53
    54

[^21]: XI
    File Edit Selection View Go Run Ter
    EXPLORER
    . .
    3
    V REPOS
    > Ansible
    > Concepts
    > notes
    6
    > Robosho-shellscripts
    M
    > roboshop-ansible
    > roboshop-ansible-roles
    > shellscripts
    v terraform \\ session 1 \\ EC2 -

[^22]: C & https://registry.terraform.io/providers/hashicorp/aws/latest/docs
    . ..
    Hashi Corp
    Terraform Registry
    Search all resources
    Browse
    Publish
    Sign-in
    Use Terraform Cloud for free 7
    Providers
    hashicorp
    aws
    Version 5.49.0 v Latest Version
    aws 8
    Overview
    Documentation
    USE PROVIDER
    AWS DOCUMENTATION
    AWS Provider
    How to use this provider
    Q Filter
    Use the Amazon Web Services (AWS) provider to interact with the many resources supported
    To install this provider, copy and paste this
    by AWS. You must configure the provider with the proper credentials before you can use it.
    code into your Terraform configuration. Then,
    un terraform init.
    aws provider
    > Guides
    Use the navigation to the left to read about the available resources. There are currently 1367
    Terraform 0.13 +
    > Functions
    resources and 557 data sources available in the provider.
    terraform {
    > ACM (Certificate Manager)
    required_providers {
    To learn the basics of Terraform using this provider, follow the hands-on get started tutorials.
    aws = {
    > ACM PCA (Certificate Manager Private
    Interact with AWS services, including Lambda, RDS, and IAM by following the AWS services
    Certificate Authority)
    source = "hashicorp/aws"
    tutorials.
    version = "5.49.0"
    > AMP (Managed Prometheus)
    > API Gateway
    > API Gateway V2
    Example Usage
    > Account Management
    provider "aws"
    > Agents for Amazon Bedrock
    # Configuration options
    Terraform 0.13 and later:
    > Amazon Bedrock
    > Amplify
    terraform {
    Copy
    > App Mesh
    required_providers {

[^23]: EXPLORER
    ansible.cfg roboshop-ansible-roles
    ! web.aws_ec2.yaml
    ec2.tf
    provider.tf .
    $ 06.
    REPOS
    terraform > session1 > EC2 > provider.tf > $ provider "aws" > \[ region
    > Ansible
    1
    terraform {
    > Concepts
    12
    required_providers {
    3
    > notes
    aws = {
    4
    source = "hashicorp/aws"
    > Robosho-shellscripts
    M
    version = "5.49.0" #AWS provider version, not terraform version
    > roboshop-ansible
    6
    > roboshop-ansible-roles
    7
    > shellscripts
    8
    terraform \\ session 1 \\ EC2
    9
    ec2.tf
    10
    provider "aws" {
    11
    region = "us-east-1"
    provider.tf
    12
    13

[^24]: IAM > Users > Create user
    Step 1
    Specify user details
    Set permissions
    Add user to an existing group or create a new one. Using groups is a best-practice way to manage user's permissions by job functions. Learn more \[
    Step 2
    Set permissions
    Permissions options
    Step 3
    Review and create
    O Add user to group
    O Copy permissions
    Attach policies directly
    Add user to an existing group, or create a new
    Copy all group memberships, attached managed
    Attach a managed policy directly to a user. As a
    group. We recommend using groups to manage
    policies, and inline policies from an existing user.
    best practice, we recommend attaching policies
    user permissions by job function.
    to a group instead. Then, add the user to the
    appropriate group.
    Permissions policies (1/1196)
    C
    Create policy \[
    Choose one or more policies to attach to your new user.
    Filter by Type
    Q Search
    All types
    <
    1 2
    3 4
    5
    6
    ...
    60
    -
    Policy name \[
    Type
    4
    Attached entities
    AccessAnalyzerServiceRolePolicy
    AWS managed
    0
    V
    + AdministratorAccess
    AWS managed - job function
    0
    0
    + AdministratorAccess-Amplify
    AWS managed
    O
    0
    + AdministratorAccess-AWSElasticB...
    AWS managed
    O

[^25]: Review and create
    Review your choices. After you create the user, you can view and download the autogenerated password, if enabled.
    User details
    User name
    Console password type
    Require password reset
    terraform
    None
    No
    Permissions summary
    <
    1 >
    Name
    Type
    4
    Used as
    4
    AdministratorAccess
    AWS managed - job function
    Permissions policy
    Tags - optional
    Tags are key-value pairs you can add to AWS resources to help identify, organize, or search for resources. Choose any tags you want to associate with this user.
    No tags associated with the resource.
    Add new tag
    You can add up to 50 more tags.
    Cancel
    Previous
    Create user

[^26]: IAM > Users
    Users (1) Info
    C
    Delete
    Create user
    An IAM user is an identity with long-term credentials that is used to interact with AWS in an account.
    Q Search
    <
    1
    User name
    Path
    Group: V Last activity
    4
    MFA
    4
    Password age v Console last s
    0
    terraform
    0

[^27]: IAM > Users > terraform
    terraform Info
    Delete
    Summary
    ARN
    Console access
    Access key 1
    arn:aws:iam: 158724841371:user/terraform
    Disabled
    Create access key
    Created
    Last console sign-in
    May 13, 2024, 13:01 (UTC+05:30)
    Permissions
    Groups
    Tags
    Security credentials
    Access Advisor
    Console sign-in
    Enable console access
    Console sign-in link
    Console password
    https://158724841371.signin.aws.amazon.com/console
    Not enabled
    Multi-factor authentication (MFA) (0)
    Remove
    Resync
    Assign MFA device
    Use MFA to increase the security of your AWS environment. Signing in with MFA requires an authentication code from an MFA device. Each user can have a maximum of 8 MFA devices assigned. Learn more \[
    Type
    Identifier
    Certifications
    Created on
    No MFA devices. Assign an MFA device to improve the security of your AWS environment
    Assign MFA device
    Access keys (0)
    Create access key
    Use access keys to send programmatic calls to AWS from the AWS CLI, AWS Tools for PowerShell, AWS SDKs, or direct AWS API calls. You can have a maximum of two access keys (active or inactive) at a time. Learn more
    No access keys. As a best practice, avoid using long-term credentials like access keys. Instead, use tools which provide short term credentials. Learn more \[
    Create access key

[^28]: IAM > Users > terraform > Create access key
    Step 1
    Access key best practices &
    Access key best practices & alternatives Info
    alternatives
    Avoid using long-term credentials like access keys to improve your security. Consider the following use cases and alternatives.
    Step 2 - optional
    Use case
    Set description tag
    Command Line Interface (CLI)
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
    . Use AWS CloudShell, a browser-based CLI, to run commands. Learn more
    . Use the AWS CLI V2 and enable authentication through a user in IAM Identity Center. Learn more \[Z
    Confirmation
    I understand the above recommendation and want to proceed to create an access key.
    Cancel
    Next

[^29]: Retrieve access keys info
    Access key
    If you lose or forget your secret access key, you cannot retrieve it. Instead, create a new access key and make the old key inactive.
    Access key
    Secret access key
    AKIASJ5F436NRYTWXT5A
    \*\*\*\*\*\*\*\*\*\*\*\*\* \* \*
    Show
    Access key best practices
    . Never store your access key in plain text, in a code repository, or in code.
    . Disable or delete access key when no longer needed.
    . Enable least-privilege permissions.
    . Rotate access keys regularly.
    For more details about managing access keys, see the best practices for managing AWS access keys.
    Download .csv file
    Done

[^30]: aws terraform user access key: X
    +
    -)
    C
    Q
    >
    This PC > Professional (E:) > AWSDevOps > Keys > aws terraform user access keys
    (+
    New v
    do
    CO
    N Sort
    View
    . .
    Home
    Name
    Date modified
    Type
    Size
    Gallery
    terraform user access keys.txt
    13-05-2024 13:07
    Text Document
    1 KB
    OneDrive - Personal
    Apps

[^31]: chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform (main)
    $ aws configure
    AWS Access Key ID \[None\] : AKIASJ5F436NRYTWX
    AWS Secret Access Key \[None\] : ikikSRqh60m72TUES PiPivXyHMjKnfODKHZLS -3
    Default region name \[None\] : us-east-1
    Default output format \[None\] :
    chowd@chowdary MINGW64 /e/awsdevops /Repos /terraform (main)

[^32]: .aws
    X
    +
    C
    Q >
    This PC > Local Disk (C:) > Users > chowd >
    .aws
    +
    New v
    A
    N Sort
    View v
    . .
    Home
    Name
    Date modified
    Type
    Size
    Gallery
    config
    13-05-2024 13:09
    File
    1 KB
    OneDrive - Personal
    credentials
    13-05-2024 13:09
    File
    1 KB
    Apps
    Desktop

[^33]: EC2
    Route 53
    B IAM
    EC2 Dashboard
    X
    Amazon Machine Images (AMIs) (2) Info
    C
    \[ Recycle Bin
    \[ EC2 Image Builder
    Actions
    EC2 Global View
    Public images
    Q Search
    Events
    devops-practice
    IX
    Clear filters
    Console-to-Code Preview
    O
    Name _
    AMI name
    AMI ID
    Source
    Instances
    RHEL-9-DevOps-Practice
    ami-090252cbe067age58
    973714476881/RHEL-9-DevOps-Practice
    Instances
    Centos-8-DevOps-Practice
    ami-Of3c7d07486cad139
    973714476881/Centos-8-DevOps-Prac...
    Instance Types
    Launch Templates
    Spot Requests
    Savings Plans
    Reserved Instances
    Dedicated Hosts
    Capacity
    Reservations New
    Select an AMI
    Images
    AMIs
    AMIC
    alog

[^34]: PS E: \\AWSDevops \\Repos> cd . \\terraform\\
    PS E: \\AWSDevops \\Repos \\terraform> cd . \\session1\\
    PS E: \\AWSDevops \\Repos \\terraform\\session1> cd . \\EC2\\
    PS E: \\AWSDevops \\Repos \\terraform\\session1\\EC2> Is

[^35]: Mode
    LastWriteTime
    Length Name
    - a-
    13-05-2024
    12:43
    0 ec2. tf
    13-05-2024
    12:43
    0 provider . tf

[^36]: EXPLORER
    catalogue.service.j2
    ansible.cfg roboshop-ansible-roles
    ! web.aws_ec2.yaml
    ec2.tf
    V REPOS
    terraform > session1 > EC2 > provider.tf > ...
    > Ansible
    1
    terraform {
    > Concepts
    2
    required_providers {
    3
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
    17
    > shellscripts
    18
    v terraform \\ session 1 \\ EC2
    19
    > .terraform
    10
    provider "aws" {
    11
    E .terraform.lock.hcl
    region = "us-east-1"
    12
    ec2.tf
    13
    provider.tf

[^37]: PS E: \\AWSDevops \\Repos \\terraform\\session1\\EC2> terraform init
    Initializing the backend. ..
    Initializing provider plugins...
    Terraform has been successfully initialized!
    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. All Terraform commands
    should now work.
    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    PS E: \\AWSDevops\\Repos \\terraform\\session1\\EC2>

[^38]: chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform/session1/EC2 (main)
    $ terraform init
    Initializing the backend. ..
    Initializing provider plugins . ..
    Terraform has been successfully initialized!
    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. Al1 Terraform commands
    should now work.
    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    chowd@chowdary MINGW64 /e/awsdevops /Repos/terraform/session1/EC2 (main)

[^39]: terraform \\ session 1 \\ EC2
    > .terraform \\ providers \\ registry.terra..
    E .terraform.lock.hcl
    ec2.tf
    provider.tf

[^40]: chowd@Chowdary MINGW64 /e/awsdevops /Repos /terraform/session1/EC2 (main)
    $ terraform plan
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols:
    create
    Terraform will perform the following actions:
    # aws_instance. web will be created
    resource "aws_instance" "web"
    ami
    "ami-Of 3c7 d07486cad139"
    arn
    =
    (known after apply)
    associate_public_ip_address
    = (known after apply)
    availability_zone
    =
    (known after apply)
    cpu_core_count
    = (known after apply)
    cpu_threads_per_core
    = (known after apply)
    disable_api_stop
    (known after apply)
    disable_api_termination
    = (known after apply)
    ebs_optimized
    = (known after apply)
    get_password_data
    = false
    host_id
    = (known after apply)
    host_resource_group_arn
    =
    (known after apply)
    i am_instance_profile
    = (known after apply)
    id
    = (known after apply)
    instance_initiated_shutdown_behavior
    = (known after apply)
    instance_lifecycle
    = (known after apply)
    instance_state
    =
    (known after apply)
    instance_type
    =
    "t2.micro"
    ipv6_address_count
    = (known after apply)
    ipv6_addresses
    = (known after apply)
    key_name
    (known after apply)
    monitoring
    = (known after apply)
    outpost_arn
    = (known after apply)
    password_data
    = (known after apply)
    placement_group
    = (known after apply)
    placement_partition_number
    = (known after apply)
    primary_network_interface_id
    = (known after apply)
    private_dns
    = (known after apply)
    private_ip
    (known after apply)
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
    (known after apply)
    + tags
    "Name" = "HelloTerraform"
    tags_al1
    "Name" = "HelloTerraform"
    tenancy
    (known after apply)
    user_data
    =
    (known after apply)
    user_data_base64
    = (known after apply)
    user_data_replace_on_change
    = false
    vpc_security_group_ids
    (known after apply)
    3
    Plan: 1 to add, 0 to change, 0 to destroy.
    Note: You didn't use the -out option to save this plan, so Terraform can't
    guarantee to take exactly these actions if you run "terraform apply"
    now.
    chowd@chowdary MINGW64 /e/awsdevops/Repos/terraform/session1/EC2 (main)

[^41]: Do you want to perform these actions?
    Terraform will perform the actions described above.
    Only 'yes' will be accepted to approve.
    Enter a value: yes
    aws_instance . web: Creating. . .
    aws_instance . web: Still creating. . .
    \[10s elapsed\]
    aws_instance . web: Still creating. . .
    \[20s elapsed\]
    aws_instance . web: Still creating. . .
    \[30s elapsed\]
    aws_instance . web: Still creating. .. \[40s elapsed\]
    aws_instance. web: Creation complete after 46s \[id=i-06572997738622ege\]
    Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
    chowd@Chowdary MINGW64 /e/awsdevops /Repos /terraform/session1/EC2 (main)

[^42]: aws
    Services
    Q Search
    \[Alt+S\]
    4
    ?
    N. Virginia
    chow
    EC2
    Route 53
    96 IAM
    EC2 Dashboard
    X
    Instances (1) Info
    C
    Connect
    Instance state
    Actions
    Launch instances
    EC2 Global View
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    < 1
    Events
    O
    Name _
    4
    Instance ID
    Instance state
    A
    Instance type
    4
    Status check
    Alarm status
    Availabil
    Console-to-Code Preview
    HelloTerraform
    i-06572997738622ege
    Running
    t2.micro
    Initializing
    View alarms +
    us-east-
    Instances

[^43]: chowd@Chowdary MINGW64 /e/awsdevops /Repos/terraform/session1/EC2 (main)
    $ terraform destroy
    aws_instance . web: Refreshing state. .. \[id=i-06572997738622ege\]
    Terraform used the selected providers to generate the following execution
    plan. Resource actions are indicated with the following symbols:
    - destroy
    Terraform will perform the following actions :
    aws_instance . web will be destroyed
    resource "aws_instance" "web" {
    ami
    =
    "ami -Of 3c7d07486cad139" -> null
    arn
    =
    "arn : aws : ec2 :us-east-1: 158724841371: instance/i-06572997738622ege" -> null
    -
    associate_public_ip_address
    =
    true -> null
    availability_zone
    "us-east-1d"
    null
    cpu_core_count
    = 1 -> null
    cpu_threads_per_core
    1 -> null
    -
    disable_api_stop
    E
    false -> null
    disable_api_termination
    E
    false
    ->
    nu 17

[^44]: Plan: 0 to add, 0 to change, 1 to destroy.
    Do you really want to destroy all resources?
    Terraform will destroy all your managed infrastructure, as shown above.
    There is no undo. Only 'yes' will be accepted to confirm.
    Enter a value: yes
    aws_instance .web: Destroying. .. \[id=i-06572997738622ege\]
    aws_instance . web: Still destroying. .. \[id=i-06572997738622ege, 10s elapsed\]
    aws_instance.web: Still destroying. . .
    \[id=1-06572997738622ege, 20s elapsed\]
    aws_instance . web: Still destroying. . .
    \[id=1-06572997738622ege, 30s elapsed\]
    aws_instance . web: Destruction complete after 32s
    Destroy complete! Resources: 1 destroyed.
    chowd@chowdary MINGW64 /e/awsdevops /Repos /terraform/session1/EC2 (main)

[^45]: Instances (1) Info
    G
    Connect
    Instance state
    V
    Q Find Instance by attribute or tag (case-sensitive)
    All states
    Name _
    Instance ID
    Instance state
    4
    Instance type
    4
    Hello Terraform
    i-06572997738622ege
    Terminated
    t2.micro

