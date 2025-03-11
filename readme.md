Iam role creation - https://docs.aws.amazon.com/AmazonS3/latest/userguide/s3-batch-replication-policies.html
https://docs.aws.amazon.com/AmazonS3/latest/userguide/batch-ops-create-job.html

```
aws s3control create-job 
--region ap-southeast-2 
--account-id 286386330048 
--operation '{"S3PutObjectTagging": { "TagSet": [{"Key":"keyOne", "Value":"ValueOne"}] }}' 
--manifest '{"Spec":{"Format":"S3BatchOperations_CSV_20180820","Fields":["Bucket","Key"]},"Location":{"ObjectArn":"arn:aws:s3:::home-lab-lh-bk/manifest.csv","ETag":"*"}}' 
--report '{"Bucket":"arn:aws:s3:::devopsnomad.com.au","Prefix":"final-reports", "Format":"Report_CSV_20180820","Enabled":true,"ReportScope":"AllTasks"}' 
--priority 10 
--role-arn arn:aws:iam::286386330048:role/airflow_role 
--client-request-token $(uuidgen) 
--description "Running from CLI using manifest from airflow" 
--no-confirmation-required
```
