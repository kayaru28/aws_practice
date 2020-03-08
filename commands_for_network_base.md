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

# security group
## sg ssh
my_ip=`curl https://checkip.amazonaws.com`
aws ec2 create-security-group --group-name ssh_access --description "Security group for SSH access" --vpc-id ${id_vpc}
aws ec2 authorize-security-group-ingress --group-id ${id_sg_ssh} --protocol tcp --port 22 --cidr ${my_ip}/32
aws ec2 authorize-security-group-ingress --group-id ${id_sg_ssh} --protocol all --source-group ${id_sg_ssh}


# internet gateway
aws ec2 create-internet-gateway
aws ec2 attach-internet-gateway --vpc-id ${id_vpc} --internet-gateway-id ${id_igw}

## rt_igw
aws ec2 create-route --route-table-id ${id_rt_igw} --destination-cidr-block 0.0.0.0/0 --gateway-id ${id_igw}
aws ec2 describe-route-tables --route-table-id ${id_rt_igw}
aws ec2 associate-route-table  --subnet-id ${id_subnet_0_1_0} --route-table-id ${id_rt_igw}
aws ec2 associate-route-table  --subnet-id ${id_subnet_0_2_0} --route-table-id ${id_rt_igw}

## public ip launch
aws ec2 modify-subnet-attribute --subnet-id ${id_subnet_0_1_0} --map-public-ip-on-launch



# route_table
aws ec2 create-route-table --vpc-id ${id_vpc}

