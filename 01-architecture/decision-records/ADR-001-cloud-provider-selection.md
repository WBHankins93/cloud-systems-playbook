# ADR-001: Cloud Provider Selection (AWS)

**Status**: Accepted  
**Date**: 2026-01-22  
**Deciders**: Platform Engineering Team  
**Tags**: foundation, cloud-provider, vendor-lock-in

---

## Context

The DataFlow Platform requires a cloud provider to host all infrastructure and services. The system must process 10M+ events/day, maintain 99.95% availability, support multi-region deployment for GDPR compliance, and operate within a $50K/month infrastructure budget.

**Key constraints**:
- Single cloud provider only (multi-cloud explicitly not an option)
- Small team (3-4 platform engineers) with limited operational capacity
- Kubernetes expertise available (team has strong K8s experience)
- Budget: $50K/month target, $75K/month hard cap
- GDPR compliance requires EU region deployment
- MVP delivery in 3 months

---

## Decision

**We will use AWS (Amazon Web Services) as our single cloud provider.**

This decision applies to all infrastructure, managed services, and platform components. All architectural decisions will be made within the AWS ecosystem.

---

## Rationale

### 1. Managed Service Maturity and Breadth

AWS provides the most mature and comprehensive managed service portfolio for our use case:

- **EKS (Elastic Kubernetes Service)**: Mature managed Kubernetes with strong ecosystem support
- **Kinesis Data Streams**: Managed event streaming service that eliminates Kafka operational burden
- **S3**: Industry-standard object storage with 11 nines durability
- **DynamoDB**: Managed NoSQL database with on-demand pricing
- **RDS**: Managed PostgreSQL with Multi-AZ for high availability
- **API Gateway**: Managed API service with built-in authentication and rate limiting

**Impact**: Reduces operational burden for small team, enables faster MVP delivery.

### 2. Cost Efficiency at Scale

AWS pricing is competitive for our workload patterns:

- **EKS**: $0.10/hour for control plane (~$73/month), node costs scale with usage
- **Kinesis**: Pay-per-shard model, auto-scaling reduces over-provisioning
- **S3**: Tiered storage with lifecycle policies enables cost optimization
- **DynamoDB**: On-demand pricing eliminates capacity planning overhead

**Projected cost at 10M events/day**: ~$50K/month (within budget target)

**Impact**: Enables system to scale within budget constraints.

### 3. Kubernetes Support and Ecosystem

AWS EKS has the most mature Kubernetes support among cloud providers:

- **EKS**: Largest ecosystem of integrations and tooling
- **Team expertise**: Team has strong Kubernetes experience (constraint alignment)
- **Portability**: Kubernetes provides some portability even within AWS ecosystem
- **Community**: Largest community and documentation base

**Impact**: Leverages team expertise, reduces learning curve, enables faster delivery.

### 4. Multi-Region Capabilities

AWS provides strong multi-region support for GDPR compliance:

- **Regions**: us-east-1 (US), eu-west-1 (EU) both well-supported
- **Data residency**: Clear data residency controls and compliance certifications
- **Cross-region networking**: VPC peering and transit gateway for inter-region connectivity
- **Regional services**: All required services available in both regions

**Impact**: Enables GDPR compliance without complex workarounds.

### 5. Compliance and Security

AWS meets our compliance requirements:

- **SOC 2**: AWS infrastructure is SOC 2 certified (supports our certification)
- **GDPR**: AWS GDPR compliance program and data processing addendum
- **Encryption**: Comprehensive encryption options (KMS, S3 encryption, etc.)
- **Audit logging**: CloudTrail provides comprehensive audit logging

**Impact**: Reduces compliance burden, enables SOC 2 certification.

---

## Consequences

### Positive

✅ **Operational simplicity**: Managed services reduce operational burden for small team  
✅ **Faster time-to-market**: Mature services enable 3-month MVP delivery  
✅ **Cost efficiency**: Competitive pricing keeps us within $50K/month budget  
✅ **Team alignment**: Leverages team's Kubernetes expertise  
✅ **Compliance**: Built-in compliance features reduce certification burden  
✅ **Ecosystem**: Largest ecosystem of tools, integrations, and community support  
✅ **Reliability**: Proven track record of high availability and durability  

### Negative

❌ **Vendor lock-in**: Deep integration with AWS services creates vendor lock-in  
❌ **Portability**: Difficult to migrate to another cloud provider without significant rework  
❌ **Cost at very high scale**: Some AWS services may become expensive at extreme scale (100M+ events/day)  
❌ **AWS-specific knowledge**: Team must develop AWS-specific expertise  
❌ **Service dependencies**: Dependent on AWS service availability and pricing changes  

### Neutral / Accepted Tradeoffs

- **Vendor lock-in accepted**: Constraint explicitly states "vendor lock-in acceptable" when managed services reduce operational burden
- **AWS-specific patterns**: Will use AWS-native patterns (e.g., Kinesis instead of Kafka) to maximize managed service benefits
- **Learning curve**: Team will need to learn AWS-specific services, but this is acceptable given managed service benefits

---

## Alternatives Considered

### Alternative: Google Cloud Platform (GCP)

**Why rejected**:
- Less mature Kubernetes support (GKE has smaller ecosystem)
- Higher cost for our workload patterns (especially data transfer)
- Team has less GCP experience
- BigQuery is excellent but we don't need it (using Snowflake)

**Tradeoff**: GCP's data analytics strengths don't align with our needs.

### Alternative: Microsoft Azure

**Why rejected**:
- AKS (Azure Kubernetes Service) less mature than EKS
- Higher cost for managed services at our scale
- Team has minimal Azure experience
- Enterprise-focused features not needed for our use case

**Tradeoff**: Azure's enterprise integration strengths don't justify higher cost and learning curve.

### Alternative: Multi-Cloud

**Why rejected**:
- Explicitly prohibited by constraint ("multi-cloud is not an option")
- Operational complexity prohibitive for 3-4 person team
- Cost: Multi-cloud networking and data transfer costs are prohibitive
- Compliance: GDPR data residency becomes more complex across clouds

**Tradeoff**: Multi-cloud would violate constraints and increase complexity beyond team capacity.

---

## Constraints That Shaped This Decision

1. **"Multi-cloud is not an option"**: Eliminated multi-cloud alternatives
2. **"Vendor lock-in acceptable"**: Made AWS lock-in acceptable tradeoff
3. **"Team size and operational capacity"**: Required managed services (AWS strength)
4. **"Kubernetes expertise available"**: Made EKS a natural fit
5. **"Budget: $50K/month target"**: Required cost-efficient provider (AWS competitive pricing)
6. **"GDPR compliance required"**: Required strong multi-region support (AWS strength)
7. **"MVP in 3 months"**: Required mature services and ecosystem (AWS strength)

---

## Implementation Notes

- All infrastructure will be provisioned in AWS
- Terraform will target AWS provider (team learning IaC, AWS provider is well-documented)
- All managed services will be AWS-native (Kinesis, S3, DynamoDB, RDS, EKS)
- Architecture will leverage AWS service integrations (e.g., Kinesis → S3, CloudWatch integration)
- Cost monitoring will use AWS Cost Explorer and billing alerts

---

## References

- [Alternatives Considered](../alternatives-considered.md#cloud-provider-selection)
- [Initial Design](../initial-design.md#architecture-overview)
- [Constraints](../../00-context/constraints.md#technical-constraints)

---

## Status History

- **2026-01-22**: Accepted - Initial decision for DataFlow Platform architecture

---

_This ADR establishes the foundation for all subsequent architectural decisions. All infrastructure, platform, and service decisions will be made within the AWS ecosystem._
