# ec2
## subnet1
aws ec2 run-instances --image-id ${id_ami_linux_standerd} --count 1 --instance-type t2.micro --key-name ${id_key_pair} --security-group-ids ${id_sg_ssh} --subnet-id ${id_subnet_0_1_0}
## subnet2
aws ec2 run-instances --image-id ${id_ami_linux_standerd} --count 1 --instance-type t2.micro --key-name ${id_key_pair} --security-group-ids ${id_sg_ssh} --subnet-id ${id_subnet_0_2_0}
## subnet3
aws ec2 run-instances --image-id ${id_ami_linux_standerd} --count 1 --instance-type t2.micro --key-name ${id_key_pair} --security-group-ids ${id_sg_ssh} --subnet-id ${id_subnet_0_3_0}
## subnet4
aws ec2 run-instances --image-id ${id_ami_linux_standerd} --count 1 --instance-type t2.micro --key-name ${id_key_pair} --security-group-ids ${id_sg_ssh} --subnet-id ${id_subnet_0_4_0}

## delete
aws ec2 terminate-instances --instance-ids ${id_instance=}


# RDS
aws ec2 create-volume --volume-type gp2 --size 1 --availability-zone ${az_a}
aws ec2 create-volume --volume-type gp2 --size 1 --availability-zone ${az_c}
aws ec2 create-volume --volume-type gp2 --size 1 --availability-zone ${az_d}

aws ec2 attach-volume --device /dev/sdf --instance-id ${id_instance} --volume-id ${id_volume}

aws ec2 detach-volume --volume-id ${id_volume}
aws ec2 delete-volume --volume-id ${id_volume} 

## instance
lsblk
sudo file -s /dev/xvdf
sudo mkfs -t xfs /dev/xvdf
sudo mkdir /data
sudo umount /data

