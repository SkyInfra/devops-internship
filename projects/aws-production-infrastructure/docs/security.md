# Security Design

## Security Groups

- `alb-sg`: Allows inbound HTTP traffic on TCP port 80.
- `app-sg`: Allows inbound TCP port 3000 from `alb-sg`.

## Instance Administration

AWS Systems Manager Session Manager is used for instance administration instead of exposing SSH to the internet.

## Credential Safety

Never commit AWS access keys, private keys, passwords, or `.env` files to this repository.
