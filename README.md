# AWS EC2 Instance Launch Script

This repository contains a Python script that uses the Boto3 library to interact with Amazon Web Services (AWS) EC2. The script launches an EC2 instance and stores its ID in a list.

## Prerequisites

Before using the script, ensure you have the following:

- **You have to install Python using the anaconda ide
 or
- you can install the python ide via normal method **

- **Boto3 library**: The AWS SDK for Python. You can install it via pip.

-  **AWS account with access keys**: Obtain your AWS Access Key ID and Secret Access Key from the AWS Management Console.

## Installation

1. Install the Boto3 library using pip:
   ```bash
   pip install boto3
   ```

2. Ensure you have configured your AWS credentials. Replace the placeholder values for `aws_access_key_id` and `aws_secret_access_key` in the script with your actual credentials.

## Script Overview

The script performs the following tasks:

1. **Establishes an EC2 resource connection** using the provided AWS credentials and region.
2. **Launches an EC2 instance** with the specified instance type and AMI ID.
3. **Stores the launched instance ID** in a list for tracking purposes.

### Python Script

```python
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
```

## Notes

- **Replace Placeholder Values**: Substitute `YOUR_AWS_ACCESS_KEY_ID` and `YOUR_AWS_SECRET_ACCESS_KEY` with your actual AWS credentials.
- **Modify Image ID**: The `ImageId` parameter specifies the Amazon Machine Image (AMI) ID. Ensure this value corresponds to a valid AMI 
