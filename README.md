# Lambda Function and S3 Integration

## 1. What is the purpose of the execution role on the Lambda function?
The **execution role** is an IAM role associated with the Lambda function that allows the function to interact with AWS services. It defines what actions the Lambda function can perform on other AWS resources (e.g., reading from an S3 bucket, writing logs to CloudWatch). This role contains **IAM policies** that grant permissions required by the Lambda function during execution.

---

## 2. What is the purpose of the resource-based policy on the Lambda function?
The **resource-based policy** on a Lambda function allows external entities (e.g., an S3 bucket) to invoke the Lambda function. It grants permissions to a specified principal (like an S3 bucket or another AWS service) to trigger the function. This policy is necessary to allow the integration between services.

---

## 3. If the function is needed to upload a file into an S3 bucket, describe:

### Needed update on the execution role:
The **execution role** must include a policy granting the Lambda function permission to perform the following actions:
- `s3:PutObject` on the destination bucket.

### New resource-based policy:
A **resource-based policy** needs to be added to the **destination S3 bucket**, granting the Lambda function's role permission to upload files. The policy must:
- Specify the Lambda function's execution role as the principal.
- Allow the action `s3:PutObject` on the bucket or specific objects within the bucket.
