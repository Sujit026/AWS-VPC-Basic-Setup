# AWS-VPC-Basic-Setup

**Overview** : - 
In this project, I designed and implemented a custom Virtual Private Cloud (VPC) architecture in AWS. The setup includes both public and private subnets with proper routing, internet access, and security configurations.

**VPC** : -   
VPC is a virtual private cloud   

<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/7e49d1cd-ca8a-4906-a4b5-4a230c5c55b4" />
 
**Subnet** : -
 
Subnet is a smaller network inside a VPC.  

Types:  
Public Subnet → Internet access  
Private Subnet → No direct internet

<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/d3e9ae28-7dc8-4cb3-ad19-e696f86ddeb5" />


**Internet Gateway (IGW)** : - 
An Internet Gateway allows communication between VPC to Internet.

<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/ae50fb7f-bb4a-45d0-8ebe-3f225cf9e4a8" />


**NAT Gateway** : - 
A NAT Gateway allows Private subnet to internet ( Only for Outbound Traffic )
<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/0e5cdeda-aefa-46c6-a099-716e558ab3ca" />


**Route Table** : - 
A Route Table decides Where traffic should go.
Internal traffic → stays in VPC
Internet traffic → goes to IGW

**Use of Route Table** : - 
Route table acts like "Traffic controller"  

<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/019eda8e-7642-4d42-8614-672fdac6f81b" />
                                                                                                 
**Subnet Association** : - 
Linking subnet to a route table  
It is needed because Because Every subnet must know Which route table to follow.  
                                                         
<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/52c56c41-803b-457f-9207-dd9b1764ce46" />  
<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/c5d601ab-edbc-4089-afbb-69f60683f16e" />

                                                             
**Security Group** : -    
A Security Group is a virtual firewall at instance level. It controls Inbound traffic and Outbound traffic using ports.  
                                   
<img width="600" height="210" alt="image" src="https://github.com/user-attachments/assets/3415e630-a99a-4ec6-81aa-cad52930b621" />


**Packet Flow in VPC** ::

**Case 1: Internet → Public EC2  ==> Internet → IGW → Route Table → Subnet → SG → EC2** ::

-The user sends a request to the Public IP of the EC2 instance.   
-The request first reaches the Internet Gateway (IGW) attached to the VPC.  
-The Internet Gateway then evaluates the route table associated with the subnet.  
-Based on the route table rules, the traffic is directed to the appropriate public subnet.  
-Once the traffic reaches the subnet, the Security Group checks whether the request is allowed.  
-If the rules permit, the request is forwarded to the EC2 instance.  

**Case 2: Private EC2 → Internet  ==> Private EC2 → Route Table → NAT GW → IGW → Internet** ::

-The EC2 instance in the private subnet initiates a request to access the internet.  
-The request is first sent to the route table associated with the private subnet.  
-The route table directs the traffic to the NAT Gateway.  
-The NAT Gateway processes the request and forwards it to the Internet Gateway (IGW).  
-The Internet Gateway then sends the request out to the internet.  

**Outcome** : - 

- Created a VPC with public and private subnets    
- Enabled internet access using Internet Gateway (IGW)    
- Configured NAT Gateway for secure outbound traffic from private subnet    
- Applied security using Security Groups    

**Learning** : - 

- Gained clear understanding of AWS VPC architecture    
- Learned practical cloud networking concepts    
- Understood how traditional networking maps to AWS   
