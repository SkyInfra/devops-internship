# AWS Production Infrastructure

A production-style AWS infrastructure project demonstrating multi-AZ networking, private compute resources, security-group-based traffic control, and application load balancing.

## Architecture Overview

The infrastructure is deployed in the AWS Asia Pacific (Mumbai) region (`ap-south-1`).

### Infrastructure Components

- **Amazon VPC:** Custom production VPC with CIDR `10.0.0.0/20`
- **Networking:** Public and private subnets across two Availability Zones
- **NAT Gateway:** Outbound internet connectivity for private resources
- **Amazon EC2:** Two private application instances
- **AWS IAM:** Instance role for Systems Manager access
- **AWS Systems Manager:** Secure instance administration without SSH
- **Security Groups:** Controlled traffic between the ALB and application instances
- **Application Load Balancer:** Internet-facing entry point for HTTP traffic
- **Target Group:** Routes requests to application instances on port `3000`
- **Health Checks:** Application health endpoint at `/health`

## Request Flow

1. A client sends an HTTP request to the Application Load Balancer.
2. The ALB forwards the request to a healthy application instance.
3. The Node.js application processes the request.
4. The application health endpoint verifies application and database connectivity.

## Validation

- Two registered targets reported Healthy.
- The target group reported zero unhealthy targets.
- The health endpoint was used to validate database connectivity.
- The application was tested through the ALB DNS name.

## Technology Stack

AWS, Amazon VPC, EC2, IAM, Systems Manager, NAT Gateway, Application Load Balancer, Security Groups, Node.js, PostgreSQL.

## Documentation and Evidence

- `architecture/` — Architecture documentation and diagrams.
- `docs/` — Networking, security, and load-balancing details.
- `screenshots/` — Evidence captured during implementation and testing.

## Future Improvements

- Provision infrastructure using Terraform.
- Add automated application deployment through a CI/CD pipeline.
- Configure centralized monitoring, alarms, and logging.
- Implement HTTPS using AWS Certificate Manager.
- Document disaster recovery and infrastructure cost controls.

## Scope

This project demonstrates a production-style infrastructure deployment. Additional automation, monitoring, TLS, and disaster recovery work would be needed before describing it as fully production-ready.