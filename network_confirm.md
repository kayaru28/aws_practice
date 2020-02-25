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