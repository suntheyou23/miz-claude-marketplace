# AI Company Plugin

An autonomous development organization plugin for Claude Code that transforms user requirements into production-ready AWS applications with minimal human intervention.

## Overview

AI Company orchestrates a complete development lifecycle from requirements gathering to deployment and project memory generation. It delivers enterprise-quality code with architecture design, cost estimates, TDD implementation, and deployment guides.

## Features

- **Autonomous Development**: Minimal human intervention required—only for requirements approval, cost approval, and final deliverable approval
- **AWS-Focused**: Designed for AWS serverless applications with built-in cost estimation and Well-Architected best practices
- **Test-Driven Development**: Implements features using TDD cycle with comprehensive unit and integration tests
- **Cost Transparency**: Provides detailed cost estimates before implementation with AWS MCP integration
- **Complete Documentation**: Generates requirements, design documents, research notes, tasks, and deployment guides
- **Project Memory**: Creates steering files for consistent future development

## Development Phases

The plugin orchestrates development through the following phases:

1. **Requirements Definition**: Gathers requirements and generates summary (user language) and detailed specification (EARS notation)
2. **Gap Analysis**: Analyzes implementation gap between requirements and existing codebase (Greenfield vs Brownfield)
3. **Design & Review**: Creates technical architecture with research, design documents, and automated review
4. **Budget Approval**: Estimates AWS costs based on usage assumptions and design
5. **Task Planning**: Breaks down design into manageable implementation tasks
6. **Implementation**: Executes tasks using Test-Driven Development
7. **Validation**: Validates implementation quality, requirements traceability, and test coverage
8. **Deliverable Approval**: Generates deployment guide and deliverable summary for user approval
9. **Steering Generation**: Extracts project patterns into steering files for future development

## Prerequisites

**System Requirements**:
- `uvx` (uv tool runner) for AWS MCP and Serena MCP servers
- AWS CLI for AWS MCP authentication

**Required Configuration**:

1. **AWS MCP** - Configure AWS credentials:
   - **Install AWS CLI**: Follow the [AWS CLI installation guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
   - **Configure credentials** using one of these methods:
     - AWS Management Console credentials (recommended): `aws login` (AWS CLI v2.32.0+)
     - SSO users: `aws configure sso`
     - IAM users: `aws configure` (provide Access Key ID and Secret Access Key)
   - **Verify authentication**: `aws sts get-caller-identity`
   - **IAM Permissions** (for non-admin users): Grant `aws-mcp:InvokeMCP` and `aws-mcp:CallReadOnlyTool`

2. **Context7 MCP** - Set API key:
   - Get your API key from [context7.com/dashboard](https://context7.com/dashboard)
   - Set environment variable: `export CONTEXT7_API_KEY=your_api_key`
   - Without API key: 60 requests/hour rate limit
   - With API key: Higher rate limits and private repository access

3. **Serena MCP** - No additional configuration required (uses project directory automatically)

**MCP Servers**:

The plugin automatically configures required MCP servers via `.mcp.json` when installed:
- **AWS MCP**: AWS documentation, pricing, and architectural guidance
- **Context7 MCP**: Library and framework documentation with version-specific API information (HTTP-based, no local installation required)
- **Serena MCP**: Codebase-wide semantic search, symbol-level navigation, and code analysis

## Installation

### Option 1: Install from GitHub (Recommended)

1. **Add the marketplace**:
   ```
   /plugin marketplace add suntheyou23/miz-claude-marketplace
   ```

2. **Install the plugin**:
   ```
   /plugin install ai-company
   ```

The plugin and its MCP servers are automatically enabled.

### Option 2: Install from Local Path

1. **Clone the repository**:
   ```bash
   git clone https://github.com/suntheyou23/miz-claude-marketplace.git
   ```

2. **Add the marketplace**:
   ```
   /plugin marketplace add /path/to/miz-claude-marketplace
   ```

3. **Install the plugin**:
   ```
   /plugin install ai-company
   ```

### Option 3: Interactive Installation

1. In Claude Code, run:
   ```
   /plugin
   ```

2. Select "Browse Plugins"

3. Find and install "ai-company"

### Verify Installation

Check that the plugin is loaded:

```
/help
```

Look for the `/ai-company` command in the output.

## Usage

### Starting a New Project

Use the `/ai-company` slash command to begin the autonomous development process:

```
/ai-company [your requirement description]
```

The command will guide you through:
1. Requirements gathering and approval
2. Design and cost estimation
3. Implementation and validation
4. Deployment preparation

### Human Interaction Points

You will be asked for approval at three key points:

1. **Requirements Approval** (Phase 1): Review and approve requirements summary
2. **Cost Approval** (Phase 4): Review and approve estimated AWS costs
3. **Deliverable Approval** (Phase 8): Review implementation summary and deploy using the provided guide

### Adding Features to Existing Projects

For projects with existing steering files (`.ai-company/steering/`), the workflow automatically adapts:

- Gap analysis evaluates integration with existing codebase (Brownfield mode)
- Design follows established patterns from steering files
- Implementation maintains consistency with existing code

## Generated Artifacts

The plugin generates the following artifacts in `.ai-company/`:

- `requirements-summary.md`: User-facing requirements overview
- `requirements-detail.md`: Detailed specification with EARS acceptance criteria
- `gap-analysis.md`: Implementation gap analysis
- `research.md`: Technical research and design decisions
- `design-document.md`: Comprehensive technical design
- `cost-estimate.md`: Detailed AWS cost estimation
- `tasks.md`: Implementation task breakdown
- `deliverable-summary.md`: Implementation summary and cost verification
- `deployment-guide.md`: Deployment instructions and verification
- `steering/`: Project memory for future development
  - `product.md`: Core capabilities and value proposition
  - `structure.md`: Directory patterns and conventions
  - `tech.md`: Tech stack and development standards

## Design Principles

- **Cognitive Load Minimization**: Only essential information at each phase
- **Type Safety**: Strong typing enforced throughout (no `any` in TypeScript)
- **Requirements Traceability**: Every component maps to specific requirements
- **AWS Best Practices**: Follows Well-Architected Framework principles
- **Test Coverage**: Unit and integration tests for all functionality

## License

MIT License

## Attribution

This plugin incorporates concepts and templates from [cc-sdd](https://github.com/gotalab/cc-sdd)

Copyright (c) 2025 gotalab
Licensed under the MIT License
