# Packer template
A packer template to configure a bamboo agent AMI for AWS

## Usage
Make sure to have [Packer](https://packer.io/) installed, then:

    export AMI_NAME="bamboo-agent-v1" # What name to use for this AMI for viewing in the web console
    export AWS_ACCESS_KEY_ID=<your access key>
    export AWS_SECRET_ACCESS_KEY=<your secret key>
    export AWS_DEFAULT_REGION=eu-central-1 # Change to your AWS region
    export SUBNET_ID=subnet-e3bef194 # VPC subnet ID for packer-created instance
    export SOURCE_AMI=ami-58cc762b # [Ubuntu cloud image](https://cloud-images.ubuntu.com/trusty/). Use 64-bit HVM SSD
    export VPC_ID=vpc-5ed4a43b # VPC ID for packer-created instance 
 
 Run from packer dir
 
    /usr/local/bin/packer build -var "description=bamboo-agent-v1" -var "aws_access_key=${AWS_ACCESS_KEY_ID}" -var "aws_secret_key=${AWS_SECRET_ACCESS_KEY}" -var "region=${AWS_DEFAULT_REGION}" -var "source_ami=${SOURCE_AMI}" -var "subnet_id=${SUBNET_ID}" -var "vpc_id=${VPC_ID}" -var "ami_name=${AMI_NAME}" bamboo-agent.json

You can change insance type and EBS volume size by modifying 
```
"instance_type": "m3.large",
```
```
"volume_size": 20,
```