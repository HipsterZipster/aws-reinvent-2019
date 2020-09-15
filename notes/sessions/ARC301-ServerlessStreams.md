# ARC301 - Serverless Stream Processing and Best Practices

Batch processing misses out on:
* Real time metrics
* Real time alerts
* Real time click-stream analytics
* Real time anomaly detection
* Real time XXXX

General Flow for Stream Processing:

Source -> Ingest -> Process -> Store -> Analyze

AWS Kinesis + AWS Lambda: Pay only for use and value

AWS Kinesis has 3 offerings:
* Data streams
* Firehose
* Analytics

## Kinesis Data Stream
* Ordered message buffer ~ 1 MB/s
* Subsecond latency
* Data needs to be consumed
* Max 5 consumers per stream

## Kinesis Firehose
* Guaranteed data delivery to destination ~ 60s latency
* Data does *not* have to be consumed
*

## Processing Kinesis Data Streams with Lambda:
* No servers to manage
* Automatically scales during reshard operations
* Only pay as the Lambda runs
* Lambda will configure a batch window for polling
* Lambda is not always the right choice:
    * stateful, sums, aggregations, buffering, etc. use Kinesis Data Analytics

## Retrying Data Stream Messages
Retry/Failure behaviors are available as a configuration in AWS Console
* Push bad messages to SQS / SNS
* max age, max retry attempts, split batch on error

## Monitoring
Iterator Age = if it's getting longer, means your processing is falling behind, could start losing messages from the queue

## Kinesis Data Analytics
* Consume from data stream or firehose in real time
* Write SQL statements to analyze the stream, provide a window to prevent continous result