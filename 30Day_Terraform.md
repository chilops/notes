---
title: 30Day_Terraform
uuid: 0d0d170a-1f0f-11ef-b323-2e97089a9920
version: 460
created: '2024-05-31T11:01:37+05:30'
tags:
  - terraform
---

***Topics:***

1. <mark style="background-color:#f8d616;">VPC - Virtual private cloud creation with HA (High Availability)<!-- {"backgroundCycleColor":"25"} --></mark>

    1. <mark>Creating VPC</mark>

    1. <mark>Creating Internet gateway(IG) and assigning it to VPC</mark>

    1. <mark>Creating a subnet with HA(High Availability)</mark>

        1. <mark>creating AZ-1 public subnet AZ-2 public subnet</mark>

        1. <mark>Creating AZ-1 private subnet AZ-2 private subnet</mark>

        1. <mark>Creating AZ-1 database subnet AZ-2 database subnet</mark>

    1. <mark>Route table creation - 3 (public, private, database) & Assigning Internet gateway to public route table</mark>

        1. <mark>Public route table & associating with public subnets(1a, 1b)</mark>

        1. <mark>Assigning Internet gateway to public route table</mark>

        1. <mark>Private route table & associating with private subnets(1a, 1b)</mark>

        1. <mark>Database route table & associating with Database subnets(1a, 1b)</mark>

1. <mark style="background-color:#f8d616;">NAT Gateway - only for outgoing traffic<!-- {"backgroundCycleColor":"25"} --></mark><!-- {"offset":1} -->

    1. <mark>Elastic IP creation</mark>

    1. <mark>NAT gateway creation</mark> 

    1. <mark>Adding NAT gateway to Private & Database route tables</mark>

\

   

\

\

\

\

# <mark style="background-color:#f8914d;">**VPC - Virtual private cloud creation with HA (High Availability)**<!-- {"backgroundCycleColor":"24"} --></mark><!-- {"collapsed":true} -->

\

<mark>**Creating VPC**</mark>

![11aa20c1-c393-441c-8526-5b5155226498.png|963](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/11aa20c1-c393-441c-8526-5b5155226498.png) [^1]

![27c8d3b8-4e14-4b02-af27-176bdb42c4ce.png|971.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/27c8d3b8-4e14-4b02-af27-176bdb42c4ce.png) [^2]

\

<mark>**Creating Internet gateway(IG) and assigning it to VPC**</mark>

![dcaf1c5d-35e4-4863-8d5c-39ba35f1a0c3.png|933](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/dcaf1c5d-35e4-4863-8d5c-39ba35f1a0c3.png) [^3]

![b86043f9-1161-44a6-9ef4-129f83c0bfac.png|996.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/b86043f9-1161-44a6-9ef4-129f83c0bfac.png) [^4]

\

![72f17851-dd78-4c60-90f7-64d006f2b7f0.png|1058.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/72f17851-dd78-4c60-90f7-64d006f2b7f0.png) [^5]

\

![f0a378b7-8a24-4f4b-b98d-b4e50291ffcd.png|1089.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/f0a378b7-8a24-4f4b-b98d-b4e50291ffcd.png) [^6]

![a63335b9-a83d-4ac3-9c6a-b0e636e735d7.png|1050.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/a63335b9-a83d-4ac3-9c6a-b0e636e735d7.png) [^7]

\

<mark>**Creating a subnet with HA(High Availability)**</mark>

\

HA Setup

At least 2 AZ resources be there

\

<mark style="background-color:#eefdd7;">**AZ-1 public subnet AZ-2 public subnet**<!-- {"backgroundCycleColor":"4"} --></mark>

AZ-1 -- 10.0.1.0/24

AZ-2 -- 10.0.2.0/24

\

<mark style="background-color:#eefdd7;">**AZ-1 private subnet AZ-2 private subnet**<!-- {"backgroundCycleColor":"4"} --></mark>

AZ-1 -- 10.0.11.0/24

AZ-2 -- 10.0.12.0/24

\

<mark style="background-color:#eefdd7;">**AZ-1 database subnet AZ-2 database subnet**<!-- {"backgroundCycleColor":"4"} --></mark>

AZ-1 -- 10.0.21.0/24

AZ-2 -- 10.0.22.0/24

\

\

<mark>**creating AZ-1 public subnet AZ-2 public subnet**</mark>

![4fdf99d8-e8bf-4a68-99d8-08acf4958809.png|728](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/4fdf99d8-e8bf-4a68-99d8-08acf4958809.png) [^8]

![0bc4c420-1310-4420-83de-53e6094a3880.png|787](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/0bc4c420-1310-4420-83de-53e6094a3880.png) [^9]

![d8302eea-d32f-424b-b76c-f929458f0a01.png|956.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/d8302eea-d32f-424b-b76c-f929458f0a01.png) [^10]

\

\

<mark>**Creating AZ-1 private subnet AZ-2 private subnet**</mark>

![ac7bf588-8d8f-4292-8751-89aecc2e3ee9.png|933.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/ac7bf588-8d8f-4292-8751-89aecc2e3ee9.png) [^11]

\

<mark>**Creating AZ-1 database subnet AZ-2 database subnet**</mark>

![2c843d4a-dbe8-4484-a415-6237eca8ecad.png|1012.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/2c843d4a-dbe8-4484-a415-6237eca8ecad.png) [^12]

\

\

<mark>**Route table creation - 3 (public, private, database) & Assigning Internet gateway to public route table**</mark>

\

<mark>**Public route table & associating with public subnets(1a, 1b)**</mark>

![ddd24adc-ef60-43f1-a16b-cf128bc30b9b.png|848](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/ddd24adc-ef60-43f1-a16b-cf128bc30b9b.png) [^13]

\

![0ff7ca32-7043-4c7b-ab4f-aeec7eda0818.png|960.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/0ff7ca32-7043-4c7b-ab4f-aeec7eda0818.png) [^14]

\

<mark>**Route table associating with public subnets(1a, 1b):**</mark>

![ef929544-2df9-4a18-9f01-3df1fba7131e.png|891.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/ef929544-2df9-4a18-9f01-3df1fba7131e.png) [^15]

![2308ca26-e19d-4f0d-a21e-14b45891f919.png|971.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/2308ca26-e19d-4f0d-a21e-14b45891f919.png) [^16]

![036980a6-6d67-4944-bc70-4bc7ea19e6cc.png|1048.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/036980a6-6d67-4944-bc70-4bc7ea19e6cc.png) [^17]

\

\

<mark>**Assigning Internet gateway to public route table:**</mark>

![d4817d7c-b463-4b35-b3e2-947817177499.png|976.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/d4817d7c-b463-4b35-b3e2-947817177499.png) [^18]

![f3fbad97-2a0e-45fc-8704-c09cc6f829ac.png|1018.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/f3fbad97-2a0e-45fc-8704-c09cc6f829ac.png) [^19]

\

![bbbae97f-d719-4520-8275-fe1a1dbd989b.png|1013.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/bbbae97f-d719-4520-8275-fe1a1dbd989b.png) [^20]

\

\

<mark>**Private route table & associating with private subnets(1a, 1b):**</mark>

\

After creation snapshot

![b2df7689-a5d4-48a5-a9dd-2e6e78ba1692.png|952.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/b2df7689-a5d4-48a5-a9dd-2e6e78ba1692.png) [^21]

\

<mark>**Database route table & associating with Database subnets(1a, 1b):**</mark>

After creation snapshot

![530b22ad-23b6-4cb3-aa5a-860559b71f08.png|933.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/530b22ad-23b6-4cb3-aa5a-860559b71f08.png) [^22]

---

# <mark style="background-color:#f8914d;">**NAT Gateway - only for outgoing traffic not incoming**<!-- {"backgroundCycleColor":"24"} --></mark>

\

We need to update packages in Database, private servers, we need to download something. We should connect internet.

outgoing is allowed..

incoming traffic is disabled...

\

<mark style="background-color:#fff7cb;">We will create NAT gateway in public subnet because it has internet connectivity(Internet Gateway) then we add it in the route tables.<!-- {"backgroundCycleColor":"3"} --></mark>

![ef2e99bf-d8c0-4271-916c-b2ae90ced979.png|911](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/ef2e99bf-d8c0-4271-916c-b2ae90ced979.png) [^23]

\

We need to create & assign Elastic IP(Static IP address) to NAT gateway ( Both NAT & Elastic IP are chargeable)

\

<mark style="background-color:#f8d616;">**Elastic IP creation**<!-- {"backgroundCycleColor":"25"} --></mark>

![bed3853f-e4f5-4837-82ab-366064dee8ba.png|948.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/bed3853f-e4f5-4837-82ab-366064dee8ba.png) [^24]

\

\

<mark style="background-color:#f8d616;">**NAT Gateway Creation**<!-- {"backgroundCycleColor":"25"} --></mark>

![f5b47842-9237-40fa-b4da-403a9f588f7e.png|1014](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/f5b47842-9237-40fa-b4da-403a9f588f7e.png) [^25]

![a63635d4-7413-49b6-80a3-88ebbfb98fa4.png|1159.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/a63635d4-7413-49b6-80a3-88ebbfb98fa4.png) [^26]

\

<mark style="background-color:#f8d616;">**Adding NAT gateway to Private & Database route tables**<!-- {"backgroundCycleColor":"25"} --></mark>

![e744c27f-ce8c-4f9e-8a35-9eabbd15db8c.png|917.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/e744c27f-ce8c-4f9e-8a35-9eabbd15db8c.png) [^27]

![8a739c90-7cf9-4509-bb9b-1ea587ba0016.png|970.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/8a739c90-7cf9-4509-bb9b-1ea587ba0016.png) [^28]

![e1de1909-18c5-458b-b037-bf4174d8adf9.png|967.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/e1de1909-18c5-458b-b037-bf4174d8adf9.png) [^29]

![cb5d5d7f-cb91-493c-aa42-03500e95aaf7.png|973.3333740234375](https://images.amplenote.com/0d0d170a-1f0f-11ef-b323-2e97089a9920/cb5d5d7f-cb91-493c-aa42-03500e95aaf7.png) [^30]

[^1]: VPC > Your VPCs > Create VPC
    Create VPC Info
    A VPC is an isolated portion of the AWS Cloud populated by AWS objects, such as Amazon EC2 instances.
    VPC settings
    Resources to create Info
    Create only the VPC resource or the VPC and other networking resources.
    O VPC only
    O VPC and more
    Name tag - optional
    Creates a tag with a key of 'Name' and a value that you specify.
    roboshop-VRC
    IPV4 CIDR block Info
    . IPV4 CIDR manual input
    O IPAM-allocated IPV4 CIDR block
    IPV4 CIDR
    10.0.0.0/16
    CIDR block size must be between /16 and /28.
    IPV6 CIDR block Info
    No IPV6 CIDR block
    O IPAM-allocated IPV6 CIDR block
    Amazon-provided IPV6 CIDR block
    O IPV6 CIDR owned by me
    Tenancy Info
    Default

[^2]: Your VPCs (1/2) Info
    Actions V
    Create VPC
    Q Search
    <
    1 >
    -
    Name
    4
    VPC ID
    4
    State
    4
    IPV4 CIDR
    IPV6 CIDR
    V
    D
    Vpc-0817 cae8968304c06
    Available
    172.31.0.0/16
    d
    V
    roboshop-vpc .
    vpc-08c03b0bed89547c2
    Available
    10.0.0.0/16
    di

[^3]: VPC > Internet gateways > Create internet gateway
    Create internet gateway info
    An internet gateway is a virtual router that connects a VPC to the internet. To create a new internet gateway specify the name
    for the gateway below.
    Internet gateway settings
    Name tag
    Creates a tag with a key of 'Name' and a value that you specify.
    roboshop-IG
    Tags - optional
    A tag is a label that you assign to an AWS resource. Each tag consists of a key and an optional value. You can use tags to search and filter
    your resources or track your AWS costs.
    Key
    Value - optional
    Q Name
    X
    Q roboshop-IG
    X
    Remove
    Add new tag
    You can add 49 more tags.
    Cancel
    Create internet gateway

[^4]: VPC > Internet gateways > igw-0490a4dd897a3cf97
    igw-0490a4dd897a3cf97 / roboshop-IG
    Actions
    Details Info
    Internet gateway ID
    State
    VPC ID
    Owner
    igw-0490add897a3cf97
    Detached
    7 158724841371
    Tags
    Manage tags
    Q Search tags
    <1 >
    Key
    Value
    Name
    roboshop-IG

[^5]: VPC > Internet gateways > igw-0490a4dd897a3cf97
    igw-0490a4dd897a3cf97 / roboshop-IG
    Actions
    Attach to VPC
    Details Info
    Detach from VPC
    Manage tags
    Internet gateway ID
    State
    VPC ID
    Owner
    igw-0490a4dd897a3cf97
    Detached
    1587248413
    Delete
    Tags
    Manage tags
    Q Search tags
    <
    1 >
    Key
    Value
    Name
    roboshop-IG

[^6]: Attach to VPC (igw-0490a4dd897a3cf97)
    Info
    VPC
    Attach an internet gateway to a VPC to enable the VPC to communicate with the internet. Specify the VPC to attach below.
    Available VPCs
    Attach the internet gateway to this VPC.
    Q vpc-08c03b0bed89547c2
    X
    D
    AWS Command Line Interface command
    Cancel
    Attach internet gateway

[^7]: igw-0490a4dd897a3cf97 / roboshop-IG
    Actions V
    Details Info
    Internet gateway ID
    State
    VPC ID
    Owner
    igw-0490a4dd897a3cf97
    Attached
    vpc-08c03b0bed89547c2 \| roboshop-
    158724841371
    Vpc

[^8]: Subnet 1 of 1
    Subnet name
    Create a tag with a key of 'Name' and a value that you specify.
    roboshop-public-1a
    The name can be up to 256 characters long.
    Availability Zone Info
    Choose the zone in which your subnet will reside, or let Amazon choose one for you.
    US East (N. Virginia) / us-east-1a
    IPV4 VPC CIDR block Info
    Choose the VPC's IPv4 CIDR block for the subnet. The subnet's IPV4 CIDR must lie within this block.
    10.0.0.0/16
    IPv4 subnet CIDR block
    10.0.1.0/24
    256 IPS
    <
    Tags - optional
    Key
    Value - optional
    Name
    X
    Q roboshop-public-1a
    X
    Remove
    Add new tag
    You can add 49 more tags.
    Remove
    Add new subnet
    Cancel
    Create subnet

[^9]: Subnet 1 of 1
    Subnet name
    Create a tag with a key of 'Name' and a value that you specify.
    roboshop-public-1b
    The name can be up to 256 characters long.
    Availability Zone Info
    Choose the zone in which your subnet will reside, or let Amazon choose one for you.
    US East (N. Virginia) / us-east-1b
    IPV4 VPC CIDR block Info
    Choose the VPC's IPV4 CIDR block for the subnet. The subnet's IPV4 CIDR must lie within this block.
    10.0.0.0/16
    IPv4 subnet CIDR block
    10.0.2.0/24
    256 IPS
    <
    >
    V

[^10]: O
    roboshop-public-1a
    subnet-0c87d5abe95aac2d4
    Available
    vpc-08c03b0bed89547c2 \| roboshop-vpc
    10.0.1.0/24
    roboshop-public-1b
    subnet-0a3ca51e018777ald
    Available
    vpc-08c03b0bed89547c2 \| roboshop-vpc
    10.0.2.0/24

[^11]: O
    roboshop-private-1a
    subnet-03da632d3613fdacf
    Available
    vpc-08c03b0bed89547c2 \| roboshop-vpc
    10.0.11.0/24
    roboshop-private-1b
    subnet-059cb986978d61ac4
    Available
    vpc-08c03bObed89547c2 \| roboshop-vpc
    10.0.12.0/24

[^12]: O
    roboshop-database-1a
    subnet-03a 10cc4cf4835cfc
    Available
    vpc-08c03b0bed89547c2 \| roboshop-vpc
    10.0.21.0/24
    O
    roboshop-database-1b
    subnet-047f0a8a 1ae 16137a
    Available
    vpc-08c03b0bed89547c2 \| roboshop-vpc
    10.0.22.0/24

[^13]: Create route table info
    A route table specifies how packets are forwarded between the subnets within your VPC, the internet, and your VPN
    connection.
    Route table settings
    Name - optional
    Create a tag with a key of 'Name' and a value that you specify.
    public-route-roboshop
    VPC
    The VPC to use for this route table.
    vpc-08c03b0bed89547c2 (roboshop-vpc)
    Tags
    A tag is a label that you assign to an AWS resource. Each tag consists of a key and an optional value. You can use tags to search and filter
    your resources or track your AWS costs.
    Key
    Value - optional
    Q Name
    X
    Q public-route-roboshop
    X
    Remove
    Add new tag
    You can add 49 more tags.
    Cancel
    Create route table

[^14]: public-route-roboshop
    rtb-06bd4cea8af7 4f6a7
    No
    vpc-08c03b0bed895

[^15]: V
    public-route-roboshop
    rtb-06bd4cea8af74f6a7
    No
    vpc-08c0360bed895
    rtb-06bd4cea8af74f6a7 / public-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Explicit subnet associations (0)
    Edit subnet associations
    Q Find subnet association
    1
    Name
    Subnet ID
    4
    IPV4 CIDR
    4
    IPV6 CIDR
    No subnet associations

[^16]: VPC > Route tables > rtb-06bd4cea8af74f6a7 > Edit subnet associations
    Edit subnet associations
    Change which subnets are associated with this route table.
    Available subnets (2/6)
    Q Filter subnet associations
    <
    1
    -
    Name
    Subnet ID
    4
    IPV4 CIDR
    IPV6 CIDR
    4
    Route table ID
    V
    roboshop-public-1a
    subnet-0c87d5abe95aac2d4
    10.0.1.0/24
    rtb-06bd4cea8af74f6a7 / public-route..
    roboshop-public-1b
    subnet-0a3ca51e018777ald
    10.0.2.0/24
    rtb-06bd4cea8af74f6a7 / public-route..
    O
    roboshop-private-1a
    subnet-03da632d3613fdacf
    10.0.11.0/24
    Main (rtb-043d374ea02fa91f4)
    O
    roboshop-private-1b
    subnet-059cb986978d61ac4
    10.0.12.0/24
    Main (rtb-043d374ea02fa91f4)
    O
    roboshop-database-1a
    subnet-03a 10cc4cf4835cfc
    10.0.21.0/24
    Main (rtb-043d374ea02fa91f4)
    roboshop-database-1b
    subnet-047f0ada 1ae 16137a
    10.0.22.0/24
    Main (rtb-043d374ea02fa91f4)
    Selected subnets
    subnet-0c87d5abe95aac2d4 / roboshop-public-1a X
    subnet-0a3ca51e018777ald / roboshop-public-1b X
    Cancel
    Save associations

[^17]: V
    public-route-roboshop/
    rtb-06bd4cea8af74f6a7
    2 subnets
    No
    vpc-08c03b0bed895
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Explicit subnet associations (2)
    Edit subnet associations
    Q Find subnet association
    <
    1 >
    Name
    Subnet ID
    4
    IPV4 CIDR
    IPV6 CIDR
    roboshop-public-1a
    subnet-0c87d5abe95aac2d4
    10.0.1.0/24
    roboshop-public-1b
    subnet-0a3ca51e018777ald
    10.0.2.0/24

[^18]: V
    public-route-roboshop
    rtb-06bd4cea8af74f6a7
    2 subnets
    No
    vpc-08c0360bed895
    rtb-06bd4cea8af74f6a7 / public-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Routes (1)
    Both
    Edit routes
    O Filter routes
    1
    Destination
    4
    Target
    4
    Status
    4
    Propagated
    10.0.0.0/16
    local
    Active
    No

[^19]: VPC > Route tables > rtb-06bd4cea8af74f6a7 > Edit routes
    Edit routes
    Destination
    Target
    Status
    Propagated
    10.0.0.0/16
    local
    Active
    No
    Q local
    X
    Q 0.0.0.0/0
    X
    Internet Gateway
    No
    Remove
    Q igw-0490a4dd897a3cf97
    X
    Add route
    Cancel
    Preview
    Save changes

[^20]: V
    public-route-roboshop
    rtb-06bd4cea8af74f6a7
    2 subnets
    N
    rtb-06bd4cea8af74f6a7 / public-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Routes (2)
    Q Filter routes
    Destination
    Target
    V
    Status
    4
    Propagated
    0.0.0.0/0
    igw-0490a4dd897a3cf97
    Active
    No
    10.0.0.0/16
    local
    Active
    No

[^21]: V
    private-route-roboshop
    rtb-0566c05bb34c139ec
    2 subnets
    No
    vpc-08c03b0bed895
    8 0 0
    rtb-0566c05bb34c139ec / private-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Explicit subnet associations (2)
    Edit subnet associations
    Q Find subnet association
    < 1 >
    Name
    4
    Subnet ID
    4
    IPV4 CIDR
    4
    IPV6 CIDR
    roboshop-private-1a
    subnet-03da632d3613fdacf
    10.0.11.0/24
    roboshop-private-1b
    subnet-059cb986978d61ac4
    10.0.12.0/24

[^22]: V
    database-route-roboshop _
    rtb-Oeccf98e1ca97f30c
    2 subnets
    No
    rtb-Oeccf98e1ca97f30c / database-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Explicit subnet associations (2)
    Edit sub
    Q Find subnet association
    Name
    Subnet ID
    IPV4 CIDR
    D
    IPV6 CIDR
    roboshop-database-1a
    subnet-03a 10cc4cf4835cfc
    10.0.21.0/24
    roboshop-database-1b
    subnet-047f0a8a 1ae 16137a
    10.0.22.0/24

[^23]: USL
    PMO
    public
    Roads
    team
    Public Affairs
    Ministers
    PMO
    Secure roads
    private roads
    incoming traffic
    Arch
    private roads
    Secure roads
    Public Affairs
    Ministers
    PMO
    Roads

[^24]: Elastic IP address allocated successfully.
    Associate this Elastic IP address
    X
    Elastic IP address 52.22.252.238
    Elastic IP addresses (1)
    G
    Actions
    Allocate Elastic IP address
    Q Find resources by attribute or tag
    <
    1
    O
    Name
    Allocated IPv4 addr... V Type
    Allocation ID
    4
    Reverse DNS record
    52.22.252.238
    Public IP
    eipalloc-018223bfaa6510106

[^25]: Create NAT gateway info
    A highly available, managed Network Address Translation (NAT) service that instances in private subnets can use to connect to
    services in other VPCs, on-premises networks, or the internet.
    NAT gateway settings
    Name - optional
    Create a tag with a key of 'Name' and a value that you specify.
    roboshop-nat
    The name can be up to 256 characters long.
    Subnet
    Select a subnet in which to create the NAT gateway.
    subnet-0c87d5abe95aac2d4 (roboshop-public-1a)
    Connectivity type
    Select a connectivity type for the NAT gateway.
    Public
    Private
    Elastic IP allocation ID Info
    Assign an Elastic IP address to the NAT gateway.
    eipalloc-018223bfaa6510106
    Allocate Elastic IP
    Additional settings Info

[^26]: NAT gateways (1) Info
    Actions
    Create NAT gateway
    Q Find resources by attribute or tag
    < 1 >
    Name
    4
    NAT gateway ID
    Connectivity... V State
    4
    State message
    D
    Primary public l...
    Primary
    O
    roboshop-nat
    nat-Oda026c51ae053848
    Public
    @ Pending
    10.0.1.2

[^27]: private-route-roboshop
    rtb-0566c05bb34c139ec
    2 subnets
    No
    vpc-08c03b0bed895
    database-route-roboshop
    rtb-Oeccf98e1ca97f30c
    2 subnets
    No
    vpc-08c03b0bed895
    rtb-0566c05bb34c139ec / private-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Routes (1)
    Both
    Edit routes
    Q Filter routes
    <
    1
    >
    Destination
    Target
    4
    Status
    Propagated
    10.0.0.0/16
    local
    Active
    No

[^28]: VPC > Route tables > rtb-0566c05bb34c139ec > Edit routes
    Edit routes
    Destination
    Target
    Status
    Propagated
    10.0.0.0/16
    local
    Active
    No
    Q local
    X
    Q 0.0.0.0/0
    X
    NAT Gateway
    No
    Remove
    Q nat-Oda026c51ae053848
    X
    Use: "nat-Oda026c51ae053848"
    Add route
    nat-0da026c51ae053848 (roboshop-nat)
    Cancel
    Preview
    Save changes

[^29]: V
    private-route-roboshop
    rtb-0566c05bb34c139ec
    2 subnets
    No
    vpc-08c0360bed895
    O
    database-route-roboshop
    rtb-Oeccf98e1ca97f30c
    2 subnets
    No
    vpc-08c0360bed895
    rtb-0566c05bb34c139ec / private-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Routes (2)
    Both
    Edit routes
    Q Filter routes
    1
    Destination
    Target
    4
    Status
    Propagated
    4
    0.0.0.0/0
    nat-0da026c51ae053848
    Active
    No
    10.0.0.0/16
    local
    Active
    No

[^30]: 0
    private-route-roboshop
    rtb-0566c05bb34c139ec
    2 subnets
    No
    vpc-08c0360bed895
    V
    database-route-roboshop
    rtb-Oeccf98e1ca97f30c
    2 subnets
    No
    vpc-08c03b0bed895
    rtb-Oeccf98e1ca97f30c / database-route-roboshop
    Details
    Routes
    Subnet associations
    Edge associations
    Route propagation
    Tags
    Routes (2)
    Both
    Edit routes
    Q Filter routes
    <
    1
    Destination
    4
    Target
    4
    Status
    4
    Propagated
    0.0.0.0/0
    nat-Oda026c5 1ae053848
    Active
    No
    10.0.0.0/16
    local
    Active
    No

