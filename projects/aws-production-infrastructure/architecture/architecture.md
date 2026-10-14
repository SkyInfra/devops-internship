# AWS Production Infrastructure Architecture

## Overview

The infrastructure runs in AWS Asia Pacific (Mumbai), `ap-south-1`, using a custom VPC with CIDR `10.0.0.0/20`.

## Main Components

- Internet-facing Application Load Balancer
- Two private EC2 application instances
- Public and private subnets across two Availability Zones
- NAT Gateways for outbound connectivity from private resources
- IAM role and AWS Systems Manager Session Manager
- Security groups restricting application access
- Target group using HTTP port 3000 and `/health`

## Request Flow

1. A client connects to the ALB over HTTP port 80.
2. The ALB forwards requests to the application target group.
3. The target group routes requests to healthy EC2 instances on port 3000.
4. The application processes requests and connects to its configured database.

## Design Goals

- Keep application instances private.
- Separate public entry points from application compute.
- Restrict application traffic to the ALB security group.
- Deploy application targets across two Availability Zones.
- Use health checks to evaluate application availability.
