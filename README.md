# webapp-iac
Infrastructure as Code (IaC) project defining a scalable AWS web application architecture using CloudFormation. 

---

## Project Structure

```text
aws-webapp-infrastructure/
├── templates/
│ ├── root.yaml # Main stack orchestrator
│ ├── network.yaml # VPC, subnets, routing
│ ├── security.yaml # Security groups
│ └── compute.yaml # EC2 instances, Auto Scaling
├── parameters/
│ └── dev.json # Development environment parameters
└── README.md
```
---
## Prerequisites
1. AWS CLI configured with credentials
2. An existing EC2 key pair named "default-key" (or update compute.yaml)
3. Basic understanding of CloudFormation

---
## Deployment
### Package :
Packaging the nested templates to S3

```bash
aws cloudformation package \
  --template-file templates/root.yaml \
  --s3-bucket 'S3_BUCKET' \
  --output-template-file packaged-root.yaml
```
### Deploy :
Deploy the stack from packaged template

```bash
aws cloudformation deploy \
  --template-file packaged-root.yaml \
  --stack-name 'STACK-NAME' \
  --parameter-overrides file://parameters/dev.json \
  --capabilities CAPABILITY_NAMED_IAM

```
`
