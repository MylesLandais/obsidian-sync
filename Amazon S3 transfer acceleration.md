tags [[awd]]
enable the put bucket accelrate configuration to speed up your transfers to S3

```aws CLI

aws s3api put-bucket-accelerate-configuration --bucket bucketname --accelerate-configuration Status=Enabled

``