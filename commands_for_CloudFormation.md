# Cloud Formation
## create   
### simple
aws cloudformation create-stack --stack-name ${name_cf_stack} --template-body file://${name_cf_template}

### with parameters
aws cloudformation create-stack --stack-name ${name_cf_stack} --template-body file://${name_cf_template} --parameters \
ParameterKey=idSubnet,ParameterValue=${id_subnet_0_4_0} \
ParameterKey=idKeyPair,ParameterValue=${id_key_pair}




