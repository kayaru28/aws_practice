# env
## Lambda
name_lambda=my_func_python
runtime_lambda=python3.6
handler_lambda=lambda_index.handler
zip_lambda=lambda_code.zip
code_lambda=lambda_index.py
arn_lambda=XXXXXXX

## DynamoDB
name_dynamodb=Music

# commands
## create Lambda
aws iam list-roles --query 'Roles[].[Arn]' --output text
zip -r ${zip_lambda} ${code_lambda} 
aws lambda create-function --function-name ${name_lambda} --role ${execution_role_lambda} --runtime ${runtime_lambda} --handler ${handler_lambda} --zip-file fileb://${zip_lambda}

## check Lambda
aws lambda list-functions
aws lambda list-functions --query "Functions[].[FunctionName]" --output text

# DynamoDB
## create table
aws dynamodb create-table \
    --table-name ${name_dynamodb} \
    --attribute-definitions \
        AttributeName=Artist,AttributeType=S \
        AttributeName=SongTitle,AttributeType=S \
    --key-schema \
        AttributeName=Artist,KeyType=HASH \
        AttributeName=SongTitle,KeyType=RANGE \
    --provisioned-throughput \
        ReadCapacityUnits=10,WriteCapacityUnits=5 \
    --stream-specification \
        StreamEnabled=true,StreamViewType=NEW_IMAGE

## event source
# neccesary: lambda role that can access to dynamo db
aws lambda create-event-source-mapping --function-name ${name_lambda} \
 --batch-size 1 --starting-position LATEST --event-source ${arn_dynamodb_stream}

## check
aws lambda list-event-source-mappings --function-name ${name_lambda}

## insert data
aws dynamodb put-item \
--table-name ${name_dynamodb}  \
--item \
    '{"Artist": {"S": "No One You Know"}, "SongTitle": {"S": "Call Me Today"}, "AlbumTitle": {"S": "Somewhat Famous"}, "Awards": {"N": "1"}}'

