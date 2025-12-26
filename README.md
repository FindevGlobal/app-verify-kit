# App Verify Kit

**Self-contained AI agents and playbooks for application documentation and test generation using production data**

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)]()

The badges display the following information: Version 2.0.0 in blue and License MIT in green. These badges visually highlight the current version and license type for App Verify Kit. The overall tone is professional and informative, supporting quick identification of key project details.

App Verify Kit provides two **fully self-contained** AI agents (instruction files) that help teams:
1. **Discover workflows** from production logs and code
2. **Generate test suites** using real production data
3. **Validate test quality** against enterprise standards

### Self-Contained Design

Each agent embeds all required knowledge directly, eliminating external dependencies:

| Agent | Embedded Knowledge |
|-------|-------------------|
| `@app-discovery` | Log chunking guidelines, log analysis workflow, workflow documentation generation |
| `@test-validator` | Test generation patterns, Java test standards, quality metrics, assertion patterns, validation rules |

## Quick Setup (30 seconds)

### Step 1: Copy Agent Files
```bash
# Create the agents directory in your project
mkdir -p .github/agents

# Copy the two agent files
cp app-verify-kit/agents/*.agent.md .github/agents/
```

### Step 2: Activate
Point your automation or assistant workflow at `.github/agents/` so it can load `@app-discovery` and `@test-validator`.

That's it! No additional configuration needed.

## Usage

### App Discovery

```
@app-discovery Analyze the logs in /path/to/production-logs/
```

The agent will:
- Survey log files and identify formats
- Handle chunking for large files (>50MB) using embedded guidelines
- Extract message patterns and samples
- Validate findings against source code
- Generate workflow documentation

### Test Generation

## Migration from Previous Version

If you had the previous multi-file version with separate `instructions/` and `prompts/` folders:

1. Delete old structure:
```bash
rm -rf .github/agents/
rm -rf instructions/
rm -rf prompts/
rm -rf collections/
```

2. Copy new self-contained agents:
```bash
mkdir -p .github/agents
cp app-verify-kit/agents/*.agent.md .github/agents/
```

All functionality is preserved - just consolidated into two files.

## Contributing

1. Fork the repository
2. Make changes to agent files
3. Test with a sample project
4. Submit a pull request

## License

MIT License - see [LICENSE](LICENSE) file for details.

---

**App Verify Kit** - Discover workflows. Generate tests. Validate quality.

*Now in a simpler, self-contained package.*

src/test/java/
├── base/
│   ├── BaseMigrationTest.java
│   ├── ProductionDataLoader.java
│   └── BusinessRuleLoader.java
├── smoke/
│   └── SmokeTests.java
├── functional/
│   ├── OrderProcessingTests.java
│   └── PaymentLifecycleTests.java
└── integration/
    └── PaymentGatewayIntegrationTests.java
```

### Quality Report
```

Quality Score: 92/100
Status: APPROVED

✓ Production data usage: 100% (35/35 tests)
✓ Business logic validation: 100%
✓ Workflow coverage: 100% (5/5 workflows)
✓ State transitions: 95% (19/20)
```

## What's Embedded in Each Agent

### app-discovery.agent.md
Contains all knowledge for:
- **Log Chunking Guidelines**: Strategies for JSON, XML, FIX, CSV, Avro, binary formats
- **Log Analysis Workflow**: Survey, format detection, sample extraction, transaction patterns
- **Workflow Documentation**: Templates for workflows, state machines, message formats, integration flows

### test-validator.agent.md
Contains all knowledge for:
- **Test Generation Process**: Base infrastructure, smoke/functional/integration test templates
- **Java Test Standards**: JUnit 5, Spring Boot Test, AssertJ, REST Assured patterns
- **Quality Metrics**: Production data usage, business logic validation, coverage analysis
- **Validation Process**: Static analysis, coverage analysis, quality review, execution readiness
- **Approval Criteria**: Score calculation, thresholds, approval/rejection rules

## Troubleshooting

**Poor discovery quality?**
- Create `copilot-instructions.md` with application context
- Ensure production logs contain real transaction data

**Tests using synthetic data?**
- Run `@test-validator` to identify issues
- Ensure workflow documentation has real examples

- Just copy two files to any project

## Requirements

- **Java**: 11+ (for generated tests)
- **Build Tool**: Maven or Gradle

## File Structure

After setup, your project will have:

```
your-project/
├── .github/
│   └── agents/
│       ├── app-discovery.agent.md      # Workflow & test generation (self-contained)
│       └── test-validator.agent.md     # Quality validation (self-contained)
└── copilot-instructions.md             # Optional: Application context
```

## Best Practice: Application Entry Point

Create a `copilot-instructions.md` in your application root to dramatically improve discovery quality:

```markdown
# Application: Order Management System

## Main Entry Points
- `OrderService.java` - Core order processing
- `PaymentGateway.java` - Payment integration

## Key Entities
- Order, Customer, Payment, Shipment

## Critical Workflows
1. Order Creation → Validation → Approval → Execution
2. Payment Processing → Confirmation → Settlement

## Integrations
- Payment Gateway (REST API)
- Inventory System (JMS)
- Notification Service (AMQS)
```

## Example Output

### Generated Test Structure
```

After app discovery:

```
@test-validator Generate integration tests for the discovered workflows
```

The agent will:
- Create `BaseMigrationTest` with production data loaders
- Generate smoke tests (5-10 tests, <2 min)
- Generate functional tests per workflow
- Generate integration tests per external system

### Test Validation
After generating tests:
```
@test-validator Validate the test suite in src/test/java/
```

The agent will:
- Check for synthetic vs. production data usage
- Verify business logic validation (not just HTTP status)
- Calculate quality score (0-100)
- Provide APPROVED / APPROVED WITH WARNINGS / REJECTED status

## Agents

| Agent | Purpose | Embedded Knowledge |
|-------|---------|-------------------|
| `@app-discovery` | Discovers workflows, state machines, and message patterns from logs and code | Log chunking, analysis, workflow documentation generation |
| `@test-validator` | Generates integration tests and validates test quality | Test generation patterns, Java test standards, quality metrics |

## Key Features

### Production Data First
- **NEVER** uses synthetic or mocked data for business scenarios
- Extracts real examples from production logs
- Validates patterns against actual application behavior

### Intelligent Log Handling
- Automatic chunking for files >50MB
- Support for JSON lines, XML, FIX protocol, CSV, Avro
- Cross-chunk pattern validation

### Quality Standards
- JUnit 5, Spring Boot Test, AssertJ, REST Assured
- Business logic validation (not just HTTP status codes)
- Descriptive assertions with context

### Self-Contained
- All knowledge embedded directly in agent files
- No external instruction file dependencies
