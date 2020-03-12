# Lambda
## create
aws iam list-roles --query 'Roles[].[Arn]' --output text
zip -r ${zip_lambda} ${code_lambda} 
aws lambda create-function --function-name ${name_lambda} --role ${execution_role_lambda} --runtime ${runtime_lambda} --handler ${handler_lambda} --zip-file fileb://${zip_lambda}

## check
aws lambda list-functions
aws lambda list-functions --query "Functions[].[FunctionName]" --output text


## delete
aws lambda delete-function --function-name ${name_lambda}

## invoke
aws lambda invoke --invocation-type Event --function-name ${name_lambda} --payload '{"key1":" こんにちは", "key2":"今晩は", "key3":"さようなら"}' outputfile.txt







