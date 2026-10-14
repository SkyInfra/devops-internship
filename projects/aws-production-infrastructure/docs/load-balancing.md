# Application Load Balancing

## Load Balancer

`PROD-ALB` is an internet-facing Application Load Balancer configured in the production VPC.

## Listener and Target Group

- Listener: HTTP port 80
- Target group: `ALB-tg`
- Target protocol and port: HTTP 3000
- Health-check path: `/health`

## Validation

During testing, both registered targets reported Healthy. The application health endpoint reported database connectivity, and the application homepage was tested through the ALB DNS name.
