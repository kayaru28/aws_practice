# VPC confirm
aws ec2 describe-vpcs --output text
aws ec2 describe-vpcs --output table
aws ec2 describe-vpcs --output text | grep VPCS | awk -v 'OFS=\t' '{print $2,$8}'

# Subnet
aws ec2 describe-subnets --output text | grep SUBNETS | awk -v 'OFS=\t' '{print $3,$6,$12,$13}'

# Security Group
aws ec2 describe-security-groups --output text | grep SECURITY