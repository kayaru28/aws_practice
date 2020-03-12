## env
name_lambda=my_func_python
runtime_lambda=python3.6
handler_lambda=lambda_index.handler
zip_lambda=lambda_code.zip
code_lambda=lambda_index.py

## create
zip -r ${zip_lambda} ${code_lambda} 

aws lambda create-function --function-name ${name_lambda} --role ${execution_role_lambda} --runtime ${runtime_lambda} --handler ${handler_lambda} --zip-file fileb://${zip_lambda}

## unit test
aws lambda invoke --invocation-type Event --function-name ${name_lambda} --payload '{"key1":" こんにちは", "key2":"今晩は", "key3":"さようなら"}' outputfile.txt

