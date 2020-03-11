# SQS
## create
aws sqs create-queue --queue-name my_queue
[--attributes <value>]
[--tags <value>]
[--cli-input-json <value>]
[--generate-cli-skeleton <value>]

## check
aws sqs list-queues
aws sqs list-queues --queue-name-prefix My

## message send
aws sqs send-message --queue-url ${url_sqs} --message-body "I'm sqs"
aws sqs send-message --queue-url ${url_sqs} --message-body "I'm sqs2"  
aws sqs send-message --queue-url ${url_sqs} --message-body "I'm sqs3"  
aws sqs send-message --queue-url ${url_sqs} --message-body "I'm sqs4"  
aws sqs send-message --queue-url ${url_sqs} --message-body "I'm sqs6"  

## message receive
aws sqs receive-message --queue-url ${url_sqs}

## message delete
aws sqs delete-message --queue-url ${url_sqs} --receipt-handle ${sqs_handle}

## delete
aws sqs delete-queue --queue-url ${url_sqs}











