# infrastructure


#### Requirements:

##### AWS Networking Setup:
1. Create Virtual Private Cloud (VPC) (Links to an external site.).
2. Create subnets (Links to an external site.) in your VPC. You must create 3 subnets, each in a different availability zone in the same region in the same VPC.
3. Create an Internet Gateway (Links to an external site.) resource and attach the Internet Gateway to the VPC.
4. Create a public route table (Links to an external site.). Attach all subnets created to the route table.
5. Create a public route in the public route table created above with destination CIDR block 0.0.0.0/0 and internet gateway created above as the target.

##### Infrastructure as Code with CloudFormation
1. Install and set up AWS command-line interface.
2. Create CloudFormation template csye6225-infra.json or csye6225-infra.yml that can be used to set up required networking resources.
3. Values should not be hardcoded in your CloudFormation template.
4. You must be able to use the same CloudFormation template in the same AWS account and region to create multiple VPCs including all of its resources (listed in the “AWS Networking Setup” section) such as subnets, internet gateway, route table, etc.

##### Commands to be used:

###### Create a CloudFormation: 
aws cloudformation create-stack --stack-name <VPCname> --template-body file://csye6225-infra.yml --parameters file://config.json --profile <environment>

- dev for Development environment
- demo for Demo environment

###### Delete a CloudFormation:
aws cloudformation delete-stack \
  --stack-name <VPCname> --profile dev

