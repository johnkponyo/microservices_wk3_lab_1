# Microservices Week 3 Lab - Cloud Formation Template

## Overview
This project demonstrates automatic scaling capabilities in AWS using CloudFormation to deploy Apache web servers that dynamically adjust capacity based on CPU load. When an instance exceeds a 50% CPU utilization threshold, the Auto Scaling Group (ASG) launches a new instance to distribute traffic effectively.

## Features
- **Dynamic Scaling**: Automatically scales based on CPU utilization (threshold: 50%)
- **Load Distribution**: Application Load Balancer distributes traffic across instances
- **Instance Identification**: Each instance responds with its unique IP address and instance ID
- **CPU Stress Testing**: Interactive button to artificially stress CPU and trigger scaling

## Architecture
- **Auto Scaling Group**:
  - Minimum Capacity: 1 instance
  - Desired Capacity: 1 instance
  - Maximum Capacity: 3 instances
- **Networking**:
  - Private Subnet: Hosts the web server instances
  - Public Subnet: Hosts the Application Load Balancer
  - NAT Gateway: Provides internet access to private instances

## Deployment
1. Upload the CloudFormation template to the AWS console or use AWS CLI
2. Specify parameters (VPC CIDR, subnet CIDRs, instance type, key pair)
3. Create the stack and wait for deployment to complete

## Usage
1. Access the web application via the Application Load Balancer URL (found in CloudFormation outputs)
2. Observe the instance information displayed on the webpage
3. Click the "Stress CPU" button to initiate a 60-second CPU stress test
4. Watch as the ASG launches new instances when CPU utilization exceeds 50%
5. Refresh the page to see different instance IDs as the ALB distributes requests

## Requirements
- AWS account with sufficient permissions
- SSH key pair (for troubleshooting)

## Troubleshooting
- If instances are not scaling up, check CloudWatch metrics to verify CPU utilization
- If the webpage doesn't load, verify security group settings and health check configuration
- Check CloudFormation and Auto Scaling Group activity for any error messages