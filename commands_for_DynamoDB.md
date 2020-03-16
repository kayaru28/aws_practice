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
        ReadCapacityUnits=10,WriteCapacityUnits=5

## status check
 aws dynamodb describe-table --table-name ${name_dynamodb} | grep TableStatus

## insert data
aws dynamodb put-item \
--table-name ${name_dynamodb}  \
--item \
    '{"Artist": {"S": "No One You Know"}, "SongTitle": {"S": "Call Me Today"}, "AlbumTitle": {"S": "Somewhat Famous"}, "Awards": {"N": "1"}}'

aws dynamodb put-item \
    --table-name ${name_dynamodb} \
    --item \
    '{"Artist": {"S": "Acme Band"}, "SongTitle": {"S": "Happy Day"}, "AlbumTitle": {"S": "Songs About Life"}, "Awards": {"N": "10"} }'
 
## get data
aws dynamodb get-item --consistent-read \
    --table-name ${name_dynamodb} \
    --key '{ "Artist": {"S": "Acme Band"}, "SongTitle": {"S": "Happy Day"}}'

aws dynamodb scan --consistent-read --table-name ${name_dynamodb}

## query

aws dynamodb query \
    --table-name ${name_dynamodb} \
    --key-condition-expression "Artist = :name" \
    --expression-attribute-values  '{":name":{"S":"Acme Band"}}'

## delete            
aws dynamodb delete-table --table-name ${name_dynamodb}


