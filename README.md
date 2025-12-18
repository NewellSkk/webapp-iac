# webapp-iac
Infrastructure as Code (IaC) project defining a scalable AWS web application architecture using CloudFormation. 

## Project Structure
aws-webapp-infrastructure/
├── templates/
│ ├── root.yaml # Main stack orchestrator
│ ├── network.yaml # VPC, subnets, routing
│ ├── security.yaml # Security groups
│ └── compute.yaml # EC2 instances, Auto Scaling
├── parameters/
│ └── dev.json # Development environment parameters
└── README.md

## Prerequisites
1. AWS CLI configured with credentials
2. An existing EC2 key pair named "default-key" (or update compute.yaml)
3. Basic understanding of CloudFormation

## Deployment

### Deploy from root template:
```bash
aws cloudformation create-stack \
  --stack-name webapp-infrastructure \
  --template-body file://templates/root.yaml \
  --parameters file://parameters/dev.json \
  --capabilities CAPABILITY_NAMED_IAM