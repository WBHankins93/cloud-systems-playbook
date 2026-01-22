# Constraints

Constraints shape decisions. These constraints are explicit, non-negotiable boundaries that every architectural and operational choice must respect.

---

## Technical Constraints

### Cloud Provider
- **Multi-cloud is not an option**: Choose a single primary cloud provider (AWS, GCP, or Azure)
- **Vendor lock-in acceptable**: Managed services are preferred over self-hosted alternatives when they reduce operational burden
- **Rationale**: Team size and operational capacity require leveraging cloud-native services

### Existing Systems
- **Legacy data warehouse integration**: Must integrate with existing Snowflake instance (cannot be replaced)
- **Customer authentication**: Existing OAuth 2.0 identity provider must be supported
- **Rationale**: Business continuity requires maintaining existing customer integrations

### Performance Requirements
- **Event processing latency**: p99 latency < 500ms from ingestion to delivery
- **API response time**: p95 < 200ms for read operations
- **Rationale**: Customer SLAs and competitive positioning

---

## Organizational Constraints

### Team Structure
- **Small platform team**: 3-4 engineers (platform + infrastructure), total engineering org ~10-12 people
- **Limited SRE coverage**: No dedicated on-call rotation; platform engineers share operational responsibilities
- **Rationale**: Startup/scale-up environment with resource constraints; cannot justify dedicated SRE team yet

### Skills and Expertise
- **Kubernetes expertise available**: Platform team has strong Kubernetes operational experience (enables K8s-first architecture)
- **Limited Terraform experience**: Team is learning infrastructure-as-code; prefer managed solutions where possible to reduce IaC complexity
- **Rationale**: Team composition shapes technology choices; leverage existing expertise, minimize learning curve for new tools

### Budget
- **Infrastructure budget**: $50K/month target, $75K/month hard cap (at 10M events/day scale)
- **Cost transparency required**: Must provide per-customer cost attribution for billing and optimization
- **Rationale**: Unit economics and profitability requirements; budget must support growth without linear cost scaling

---

## Regulatory and Compliance Constraints

### Data Protection
- **GDPR compliance required**: EU customer data must remain in EU regions
- **CCPA compliance required**: California customer data handling requirements
- **Data residency**: Customer data cannot leave designated regions without explicit consent
- **Rationale**: Legal and contractual obligations

### Security Standards
- **SOC 2 Type II certification**: Must maintain certification (annual audit)
- **Encryption at rest and in transit**: Non-negotiable for all customer data
- **Audit logging**: All data access must be logged and retained for 90 days minimum
- **Rationale**: Enterprise customer requirements

### Access Controls
- **Least privilege**: All access must follow least-privilege principles
- **MFA required**: Multi-factor authentication mandatory for all production access
- **Rationale**: Security best practices and compliance requirements

---

## Operational Constraints

### Deployment Windows
- **Zero-downtime deployments**: System must remain available during deployments
- **Rollback capability**: Must be able to rollback within 5 minutes
- **Rationale**: High-availability SLA requirements

### Observability
- **Limited third-party tools**: Budget constraints limit observability tooling spend
- **Self-service debugging**: Engineers must be able to debug issues without escalating to specialists
- **Rationale**: Team size and operational model

### Change Management
- **GitOps workflow required**: All infrastructure changes must go through Git-based workflows
- **Approval gates**: Production deployments require peer review
- **Rationale**: Risk management and auditability

---

## Time Constraints

### Initial Delivery
- **MVP in 3 months**: Core event ingestion and processing operational (basic reliability, no full compliance suite)
- **Full platform in 6 months**: Complete platform with all reliability, security, and compliance controls
- **Rationale**: Business timeline and customer commitments; MVP focuses on functional delivery, full platform adds operational maturity

### Ongoing Evolution
- **Incremental improvements**: System will evolve over time; no "big bang" rewrites
- **Backward compatibility**: Changes must maintain API compatibility for 12 months
- **Rationale**: Customer stability and operational continuity

---

## Architectural Constraints

### Technology Choices
- **Container-first**: All applications must be containerized
- **Kubernetes orchestration**: Use Kubernetes for container orchestration
- **Managed databases preferred**: Prefer managed database services over self-hosted
- **Rationale**: Operational simplicity and team expertise

### Data Architecture
- **Event-driven architecture**: System must be event-driven to support real-time processing
- **Eventual consistency acceptable**: Strong consistency not required for all use cases
- **Rationale**: Performance and scalability requirements

---

## Constraints That Create Tradeoffs

These constraints create the tension points where senior engineering judgment is required:

1. **Cost vs. Performance**: Budget constraints vs. latency requirements
2. **Simplicity vs. Flexibility**: Managed services vs. custom solutions
3. **Speed vs. Safety**: Rapid delivery vs. comprehensive reliability controls
4. **Compliance vs. Velocity**: Security requirements vs. deployment frequency
5. **Scale vs. Cost**: Growth requirements vs. budget limitations

Every decision in this system navigates these constraints explicitly.

---

_Constraints are not limitations—they are the guardrails that ensure decisions are grounded in reality._
