# Senior Backend Engineer — Nimbus Technologies, Seattle, WA

**Dates:** March 2021 – Present

Backend engineering lead for the Core Platform team at Nimbus Technologies, a Series D developer-tools company (400 employees). Responsible for the API gateway, service mesh, and internal developer platform serving 60+ microservices across three AWS regions.

## Core Competencies and Technologies

- Go, Python, Rust (prototyping)
- Kubernetes (EKS), Helm, Kustomize
- AWS (ECS, Lambda, DynamoDB, SQS, S3, CloudFront, IAM)
- Terraform, Pulumi
- gRPC, REST, GraphQL
- PostgreSQL, Redis, DynamoDB
- Datadog, PagerDuty, OpenTelemetry
- GitHub Actions, ArgoCD
- Kafka, SQS

## Responsibilities and Achievements

- Lead a team of 5 engineers building and maintaining the API gateway handling 2.4B requests/month with p99 latency under 45ms
- Designed and migrated the service mesh from Linkerd to Istio, reducing cross-service auth configuration from 3 days to 15 minutes per new service
- Built an internal developer platform (IDP) with self-service provisioning that cut new-service onboarding from 2 weeks to 4 hours
- Reduced AWS infrastructure costs by 31% ($840K/year) through right-sizing, spot instance adoption, and eliminating idle resources
- Implemented distributed tracing with OpenTelemetry across 60+ services, reducing mean time to resolution (MTTR) for production incidents from 47 minutes to 12 minutes
- Mentored 3 junior engineers through promotion to mid-level; designed the team's onboarding curriculum and technical interview loop
- Drove adoption of Terraform modules across the org, replacing 14 hand-maintained CloudFormation stacks with a shared module registry
- Led quarterly chaos engineering exercises that surfaced 8 critical single-points-of-failure before they caused outages
