https://qiita.com/takachan/items/421928dc61c51af97fb1

# check
aws ec2 describe-instances

aws ec2 describe-instances | jq '.Reservations[].Instances[] | {InstanceId, Tags}'

#AMI check
aws ec2 describe-images --owners self | jq '.Images[] | {Name, ImageId}'


