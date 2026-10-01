# Compute and Scaling Architecture

## Requirements
- Survive individual EC2 instance failure
- Tolerate loss of one Availability Zone
- Prevent direct internet access to EC2
- Automatically respond to changing demand

## Compute
Service: Amazon EC2

Placement:
Private application subnets across two AZs

## Load Balancing
Application Load Balancer

Internet-facing: Yes

Targets:
Auto Scaling Group instances

## Health Checks
Path: /health

Why application-level health checks were selected:

## Auto Scaling
Minimum: 2
Desired: 2
Maximum: 6

Scaling strategy:

## Failure Analysis

### Instance Failure
Detection:
Recovery:
Customer impact:

### Availability Zone Failure
Detection:
Recovery:
Remaining risk:

### Traffic Spike
Detection:
Scaling response:
Potential bottlenecks:

## Architecture Trade-offs

### Why Auto Scaling instead of fixed EC2 capacity?

### Why private EC2 instances?

### Why deploy across two AZs?

## Future Improvements
