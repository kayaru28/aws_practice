# VPC create
aws ec2 create-vpc --cidr-block 10.0.0.0/16

# set VPC tag
aws ec2 create-tags --resources ${id_vpc} --tags Key=Name,Value=BaseVPC
>update
aws ec2 create-tags --resources ${id_vpc} --tags Key=Name,Value=vpc_base

# create subnet
aws ec2 create-subnet --vpc-id ${id_vpc} --cidr-block 10.0.1.0/24
aws ec2 create-subnet --vpc-id ${id_vpc} --cidr-block 10.0.2.0/24
aws ec2 create-subnet --vpc-id ${id_vpc} --cidr-block 10.0.3.0/24
aws ec2 create-subnet --vpc-id ${id_vpc} --cidr-block 10.0.4.0/24





# memo

# VPC confirm
aws ec2 describe-vpcs --output text
aws ec2 describe-vpcs --output table
aws ec2 describe-vpcs --output text | grep VPCS | awk -v 'OFS=\t' '{print $2,$8}'
aws ec2 delete-vpc --vpc-id

# Subnet
aws ec2 describe-subnets --output text | grep SUBNETS | awk -v 'OFS=\t' '{print $3,$6,$12,$13}'
aws ec2  delete-subnet --subnet-id ${SUBNETID}

# route table
aws ec2 describe-route-tables
aws ec2 describe-route-tables --output json | grep RouteTableId
aws ec2 delete-route-table --route-table-id ${ROUTETABLEID}

# Security Group
aws ec2 describe-security-groups --output text | grep SECURITY

# Internet gateway
aws ec2 describe-internet-gateways --output table
aws ec2 describe-internet-gateways --output json | grep InternetGatewayId
aws ec2 describe-internet-gateways --output json | grep Id

aws ec2 detach-internet-gateway --internet-gateway-id ${IGWID} --vpc-id ${VPCID}
aws ec2 delete-internet-gateway --internet-gateway-id ${IGWID}

# EIP
aws ec2 describe-addresses

# ELB