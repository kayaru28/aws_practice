# env
name_lambda=my_func_python
runtime_lambda=python3.6
handler_lambda=lambda_index.handler
zip_lambda=lambda_code.zip
code_lambda=lambda_index.py

name_bucket=test-relation-with-lambda-20200315
arn_lambda=XXXXXXX
setting_json=setting_for_lambda_by_s3.json

# commands
## create Lambda
aws iam list-roles --query 'Roles[].[Arn]' --output text
zip -r ${zip_lambda} ${code_lambda} 
aws lambda create-function --function-name ${name_lambda} --role ${execution_role_lambda} --runtime ${runtime_lambda} --handler ${handler_lambda} --zip-file fileb://${zip_lambda}

## check Lambda
aws lambda list-functions
aws lambda list-functions --query "Functions[].[FunctionName]" --output text

## create s3
aws s3 mb s3://${name_bucket}

## check S3
aws s3 ls

## add permission of accessing to Lambda function to S3
aws lambda add-permission --function-name ${name_lambda} --statement-id "s3-put-event" --action "lambda:InvokeFunction" --principal "s3.amazonaws.com" --source-arn "arn:aws:s3:::${name_bucket}"

### check
aws lambda get-policy --function-name ${name_lambda}

## s3 setting for nortigication of event to Lambda
aws s3api put-bucket-notification-configuration --bucket "${name_bucket}" --notification-configuration file://${setting_json}

### setting_for_lambda_by_s3.json
{
        "LambdaFunctionConfigurations": [
                {
                        "LambdaFunctionArn"XXXXXXXXXXXXXXX,
                        "Events": ["s3:ObjectCreated:Put"]
                }
        ]
}

### check
aws s3api get-bucket-notification-configuration --bucket ${name_bucket}

## delete
aws lambda remove-permission --function-name ${name_lambda} --statement-id "s3-put-event"
aws s3api put-bucket-notification-configuration --bucket ${name_bucket} --notification-configuration "{}"







