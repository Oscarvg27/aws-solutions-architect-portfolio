### ADR-001 — Multi-AZ NAT Architecture

Decision:
Use one NAT Gateway per Availability Zone in production.

Reason:
Avoid creating a cross-AZ egress dependency.

Trade-off:
Higher availability at higher cost.

Alternative:
A single NAT Gateway may be appropriate for a cost-sensitive
development environment.

### ADR-002 — S3 Private Connectivity

Decision:
Use an S3 Gateway VPC Endpoint.

Reason:
Application-to-S3 traffic does not require the NAT path.

### ADR-003 — Database Internet Access

Decision:
Database subnets receive no default internet route.

Reason:
The database has no requirement for direct internet connectivity.
----
# Failure analysis 

Failure                 Expected behavior
────────────────────────────────────────────────
EC2 instance fails      Replacement handles failure
AZ-A fails              AZ-B application remains
NAT-A fails             AZ-B retains NAT-B egress
Internet path fails     S3 endpoint remains independent of NAT
DB exposed to internet  Prevented by routing + SG architecture
