# Cost Estimate

**Note**: This document should be written in the user's language specified in requirements-detail.md for human review and approval.

## Summary

**Project**: [Project Name]

### Single-Phase System
- **Estimated Monthly Cost**: $[amount] USD
- **Estimated Annual Cost**: $[amount] USD

### Multi-Phase System
| Phase | Monthly Cost | Duration | Total Phase Cost |
|-------|--------------|----------|------------------|
| Initial | $[amount] USD | [X] months | $[amount] USD |
| Growth | $[amount] USD | [X] months | $[amount] USD |
| Stable | $[amount] USD | Ongoing | N/A |

**Total First Year Estimate**: $[amount] USD

## Usage Assumptions

### User Scale
- Initial Phase: [number] users, [timeframe]
- Growth Phase: [number] users, [timeframe]
- Stable Phase: [number] users, ongoing

### Usage Patterns
- Access frequency: [description]
- Session duration: [description]
- Data operations per session: [description]
- Peak usage times: [description]
- Seasonality: [description]
- Storage retention: [description]

### Derived Technical Metrics

**Calculation Methodology**:
[Explain how user-provided information was converted to technical metrics]

Examples:
- Lambda invocations: [calculation]
- DynamoDB operations: [calculation]
- S3 storage: [calculation]
- API Gateway requests: [calculation]

## Pricing Context

- **Pricing Date**: [date]
- **Region**: [AWS region]
- **Pricing Model**: On-demand (Reserved instances and savings plans not included)

## Detailed Cost Breakdown

### Single-Phase System

| AWS Service | Resource Description | Usage Metric | Unit Price | Monthly Cost |
|-------------|---------------------|--------------|------------|--------------|
| [Service] | [Description] | [Metric] | $[price] | $[cost] |
| [Service] | [Description] | [Metric] | $[price] | $[cost] |

### Multi-Phase System

#### Initial Phase

| AWS Service | Resource Description | Usage Metric | Unit Price | Monthly Cost |
|-------------|---------------------|--------------|------------|--------------|
| [Service] | [Description] | [Metric] | $[price] | $[cost] |

#### Growth Phase

| AWS Service | Resource Description | Usage Metric | Unit Price | Monthly Cost |
|-------------|---------------------|--------------|------------|--------------|
| [Service] | [Description] | [Metric] | $[price] | $[cost] |

#### Stable Phase

| AWS Service | Resource Description | Usage Metric | Unit Price | Monthly Cost |
|-------------|---------------------|--------------|------------|--------------|
| [Service] | [Description] | [Metric] | $[price] | $[cost] |

## Cost by Category

### Single-Phase or Initial Phase
- **Compute**: $[amount] USD
- **Storage**: $[amount] USD
- **Database**: $[amount] USD
- **Networking**: $[amount] USD
- **Other Services**: $[amount] USD
- **Total**: $[amount] USD

### Growth Phase (if applicable)
- **Compute**: $[amount] USD
- **Storage**: $[amount] USD
- **Database**: $[amount] USD
- **Networking**: $[amount] USD
- **Other Services**: $[amount] USD
- **Total**: $[amount] USD

### Stable Phase (if applicable)
- **Compute**: $[amount] USD
- **Storage**: $[amount] USD
- **Database**: $[amount] USD
- **Networking**: $[amount] USD
- **Other Services**: $[amount] USD
- **Total**: $[amount] USD

## Cost Optimization Opportunities

- Reserved instances for predictable workloads: [specific recommendations]
- Savings plans for compute: [specific recommendations]
- S3 lifecycle policies: [specific recommendations]
- Right-sizing recommendations: [specific recommendations]
- Cost anomaly detection setup: [recommendations]
