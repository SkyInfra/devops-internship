# Networking Design

The project uses a custom VPC with CIDR `10.0.0.0/20` and subnets distributed across two Availability Zones.

Public subnets host the internet-facing load balancer. Private subnets host application instances. NAT Gateways provide outbound connectivity from private resources when required.

## Key Design Principles

- Separate public and private resources.
- Distribute application targets across two Availability Zones.
- Restrict unnecessary inbound access.
- Keep application instances without public IP addresses.
