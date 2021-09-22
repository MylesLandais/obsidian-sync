
Uploading and copying objects using multipart upload

Multipart upload allows you to upload a single object as a set of parts. Each part is a contiguous portion of the object's data. You can upload these object parts independently and in any order. If transmission of any part fails, you can retransmit that part without affecting other parts. After all parts of your object are uploaded, Amazon S3 assembles these parts and creates the object. In general, when your object size reaches 100 MB, you should consider using multipart uploads instead of uploading the object in a single operation.

Data Security

SSE-C
Using server-side encryption with customer-provided encryption keys (SSE-C) allows you to set your own encryption keys

SSE-KMS
service that combines secure, highly available hardware and software to provide a key management system scaled for the cloud

CORS
https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html
