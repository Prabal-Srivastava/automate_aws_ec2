# AWS EC2 Instance Launch Script

This repository contains a Python script that uses the Boto3 library to interact with Amazon Web Services (AWS) EC2. The script launches an EC2 instance and stores its ID in a list.

## Prerequisites

- Python 3.x
- Boto3 library
- AWS account with access keys

## Installation

1. Install the Boto3 library using pip:
   ```bash
   pip install boto3

# Create an EC2 resource object with specific AWS credentials and region
  import boto3

# Create an EC2 resource object with specific AWS credentials and region
ec2 = boto3.resource(
    service_name="ec2",
    region_name="ap-south-1",
    aws_access_key_id="YOUR_AWS_ACCESS_KEY_ID",
    aws_secret_access_key="YOUR_AWS_SECRET_ACCESS_KEY"
)

# Define a function to launch an EC2 instance
def ec2_launch():
    myec2 = ec2.create_instances(
        InstanceType="t2.micro",  # Specify the instance type
        ImageId="ami-0fd05997b4dff7aac",  # Specify the image ID
        MinCount=1,  # Minimum number of instances to launch
        MaxCount=1  # Maximum number of instances to launch
    )
    return myec2

# Initialize an empty list to store instance IDs
OSlist = []

# Launch an EC2 instance and append its ID to the list
OSlist.append(ec2_launch()[0].id)

#note : -
Replace the placeholder values for aws_access_key_id and aws_secret_access_key with your actual AWS credentials in the script.
