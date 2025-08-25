# OODA + Claude Code Integration Examples

Practical examples demonstrating how OODA methodology enhances Claude Code effectiveness through systematic decision-making and execution patterns.

## Overview

This document provides concrete examples of integrating the OODA Loop (Observe, Orient, Decide, Act) with Claude Code best practices to create more effective agentic coding workflows. Each example shows how the OODA phases enhance different aspects of software development.

## Integration Pattern Framework

### OODA Phase Mapping to Claude Code Features

| OODA Phase | Claude Code Features | Primary Benefits |
|------------|---------------------|------------------|
| **Observe** | Context gathering, codebase analysis, tool discovery | Comprehensive situational awareness |
| **Orient** | Pattern recognition, architectural analysis, option generation | Strategic thinking and planning |
| **Decide** | Approach selection, priority setting, resource allocation | Optimal solution selection |
| **Act** | Implementation execution, testing, validation | Precise implementation with quality |

## Example 1: Adaptive Intelligence Branch Check-in Command

### Scenario
Implementing a sophisticated GitHub branch check-in slash command that demonstrates adaptive intelligence - automatically scaling from simple direct execution to full OODA methodology based on scenario complexity.

### OODA-Enhanced Command Design

#### Intelligence Assessment Framework
The command uses intelligent triggers to determine the appropriate level of systematic analysis:

**Simple Scenarios (Direct Execution)**
- < 10 files changed
- No merge conflicts  
- All tests passing
- Documentation/configuration changes
- Feature branches with low risk

**Complex Scenarios (OODA Activation)**  
- 10-50 files changed
- Integration with multiple systems
- New dependencies or architectural changes
- Some test failures requiring analysis
- Performance or security implications

**Critical Scenarios (Full OODA with Validation)**
- > 50 files or critical system changes
- Production/release branch modifications  
- Breaking changes to APIs or schemas
- Security-sensitive modifications
- High-impact performance changes

#### Adaptive OODA Implementation

```bash
# Simple scenario - Direct execution
/branch-checkin "docs: fix typo in README"
# Output: ✓ Simple scenario detected - executing direct workflow (3.2s)

# Complex scenario - OODA activation  
/branch-checkin "feat: implement real-time notification system"
# Output: ⚠️ Complex scenario detected - activating OODA methodology

# Critical scenario - Full validation
/branch-checkin "feat!: migrate to new payment API"  
# Output: 🔴 Critical scenario detected - full OODA with enhanced validation
```

#### Phase 1: Observe (Intelligent Assessment)

**Automated Context Gathering**
```bash
OBSERVE Phase - Intelligence Collection:
├── Git Repository Analysis
│   ├── Files changed: 23 files across 8 directories
│   ├── Lines modified: 1,247 additions, 892 deletions
│   ├── Merge conflicts: None detected
│   ├── Branch status: 5 commits ahead of main, 2 behind  
│   └── Recent activity: 3 contributors, last 48 hours
├── Code Quality Assessment
│   ├── Test coverage: 87% (target >90%)
│   ├── Linting issues: 3 warnings, 0 errors
│   ├── TypeScript compilation: Success with 2 warnings
│   ├── Security scan: 1 medium vulnerability detected
│   └── Performance metrics: Within acceptable thresholds
├── Dependency Analysis  
│   ├── New dependencies: socket.io, redis
│   ├── Version updates: express 4.18.1 → 4.18.2  
│   ├── Vulnerability scan: 1 transitive CVE flagged
│   └── License compatibility: All MIT compatible
└── Integration Impact
    ├── Database changes: 2 new tables, 1 index
    ├── API modifications: 5 new endpoints
    ├── External services: WebSocket, Redis integration
    └── Configuration: Environment variables, Docker
```

#### Phase 2: Orient (Strategic Analysis)

**Risk Assessment and Strategy Formulation**
```bash
ORIENT Phase - Strategic Analysis:
├── Risk Matrix Evaluation
│   ├── Technical Risk: MEDIUM
│   │   └── Real-time features require careful architecture
│   ├── Integration Risk: HIGH
│   │   └── Multiple service dependencies introduced
│   ├── Security Risk: HIGH  
│   │   └── WebSocket authentication needs validation
│   └── Performance Risk: MEDIUM
│       └── Connection scaling may impact resources
├── Architecture Impact Analysis
│   ├── System Dependencies
│   │   ├── Notification service integration
│   │   ├── WebSocket server infrastructure  
│   │   ├── Redis pub/sub messaging
│   │   └── Database schema evolution
│   ├── Testing Strategy Options
│   │   ├── Unit + Integration (fast, moderate coverage)
│   │   ├── Full end-to-end (comprehensive, slower)  
│   │   └── Progressive staged (recommended balance)
│   └── Deployment Considerations
│       ├── Blue-green deployment for zero downtime
│       ├── Feature flags for gradual rollout
│       └── Monitoring for real-time performance
└── Strategic Options Evaluation
    ├── Option A: Direct commit (high risk)
    ├── Option B: Multi-commit atomic (recommended)
    └── Option C: Feature branch staging (safest)
```

#### Phase 3: Decide (Execution Planning)

**Decision Framework and Planning**
```bash
DECIDE Phase - Execution Strategy:
├── Selected Approach: Multi-commit Progressive Deployment
├── Commit Strategy: Logical Separation  
│   ├── Commit 1: Database schema and migrations
│   ├── Commit 2: Backend service implementation
│   ├── Commit 3: WebSocket server integration
│   └── Commit 4: Frontend components and testing
├── Quality Gates Configuration
│   ├── Test coverage: Must maintain >85%
│   ├── Security: No critical/high vulnerabilities  
│   ├── Performance: <10% regression tolerance
│   └── Integration: All services must be operational
├── Validation Sequence
│   ├── Pre-commit: Linting, formatting, security scan
│   ├── Testing: Unit (45s) + Integration (90s) + E2E (3m)
│   ├── Quality: Coverage, complexity, maintainability  
│   └── Deployment: Staged rollout with monitoring
└── Risk Mitigation Plan
    ├── Feature flag: real_time_notifications (default: off)
    ├── Circuit breaker: Connection limit protection
    ├── Monitoring: Custom metrics and alerting  
    └── Rollback: Documented reversion procedures
```

#### Phase 4: Act (Precision Implementation)

**Systematic Execution with Quality Gates**
```bash
ACT Phase - Military Precision Execution:

├── Environment Preparation
│   ├── ✓ Stash uncommitted work (0 items)
│   ├── ✓ Fetch latest remote changes
│   ├── ✓ Validate branch up-to-date with main
│   └── ✓ Create safety backup branch
├── Pre-commit Validation Suite  
│   ├── ✓ TypeScript compilation (2.1s)
│   ├── ✓ ESLint + Prettier (4.6s) - 3 warnings fixed
│   ├── ✓ Security scan (4.3s) - 1 medium issue flagged
│   ├── ✓ Dependency audit (2.1s) 
│   └── ✓ Sensitive data check (0.8s)
├── Comprehensive Testing Pipeline
│   ├── ✓ Unit tests (43.2s) - 156/156 passing
│   ├── ✓ Integration tests (87.1s) - 23/23 passing
│   ├── ✓ Security tests (31.5s) - WebSocket auth validated
│   ├── ✓ Performance tests (2m 15s) - Metrics within SLA
│   └── ✓ Code coverage (5.1s) - 89.3% maintained
├── Intelligent Commit Creation
│   ├── ✓ Smart file staging (excluded logs, node_modules)
│   ├── ✓ Semantic commit messages generated
│   ├── ✓ Co-authored-by tags added (2 contributors)
│   ├── ✓ Issue references linked (#123, #145)
│   └── ✓ Conventional commit format validated
├── Advanced Branch Management
│   ├── ✓ Rebase onto latest main (no conflicts)
│   ├── ✓ Atomic commit verification  
│   ├── ✓ Branch protection compliance
│   └── ✓ Merge readiness validation
├── GitHub Integration Excellence
│   ├── ✓ Push to remote with CI trigger
│   ├── ✓ Pull request auto-creation
│   │   ├── Title: Generated from commit pattern
│   │   ├── Description: Technical details + checklist
│   │   ├── Labels: enhancement, real-time, security-review
│   │   ├── Reviewers: @backend-team, @security-team  
│   │   └── Milestone: v2.1.0 linked
│   ├── ✓ Required checks configuration
│   └── ✓ Branch protection enforcement
└── Post-commit Monitoring
    ├── ✓ CI/CD pipeline monitoring activated
    ├── ✓ Code quality metrics updated
    ├── ✓ Security scan scheduled  
    ├── ✓ Performance baseline established
    └── ✓ Team notification workflow triggered

✅ EXECUTION COMPLETED WITH MILITARY PRECISION
═════════════════════════════════════════════════════════
📊 Results: 4 commits, 23 files, 187 tests passed, 89.3% coverage
🎯 Quality: All 7 gates passed, 1 security issue for review  
⚡ Speed: 4m 23s total (optimized for complexity level)
🔗 PR: https://github.com/org/repo/pull/156 ready for review
```

**Adaptive Intelligence Learning**
```bash
LEARNING PHASE - Continuous Improvement:
├── Pattern Recognition
│   ├── Real-time features typically require full OODA
│   ├── WebSocket security validation is always critical  
│   ├── Multi-service integration benefits from staged commits
│   └── Performance testing caught 3 issues early
├── Threshold Optimization
│   ├── File count threshold accurate for this project type
│   ├── Security scanning time acceptable for team workflow
│   ├── Test execution time within productivity bounds
│   └── Quality gate strictness appropriate for criticality
├── Team Workflow Insights
│   ├── Backend team prefers technical PR descriptions
│   ├── Security reviews needed for authentication changes
│   ├── Performance regression monitoring is valuable
│   └── Feature flags enable safer deployments
└── Methodology Refinement
    ├── OODA activation criteria proven accurate
    ├── Risk assessment matrix needs minor calibration
    ├── Quality gates prevented 2 potential production issues
    └── Execution time acceptable for complex scenarios
```

### Command Usage Patterns

#### Progressive Complexity Examples

**Simple Scenario - Documentation Update**
```bash
/branch-checkin "docs: update installation instructions"

# Automatic assessment: Simple scenario detected
# Execution: Direct workflow (5-10 seconds)
# No OODA activation needed
```

**Complex Scenario - Feature Implementation**  
```bash
/branch-checkin "feat: add user authentication with OAuth2"

# Automatic assessment: Complex scenario detected  
# OODA activation: Orient and Decide phases engaged
# Execution: Systematic workflow with quality gates (2-4 minutes)
```

**Critical Scenario - Production Hotfix**
```bash
/branch-checkin "hotfix: resolve payment processing memory leak"

# Automatic assessment: Critical scenario detected
# Full OODA: All phases with enhanced validation
# Execution: Comprehensive workflow with extensive monitoring (5-8 minutes)
```

**Learning Mode - Educational Usage**
```bash
/branch-checkin --ooda "chore: update package dependencies"

# Forced OODA: Full methodology on simple change
# Educational value: Demonstrates systematic thinking
# Builds team competency in OODA methodology
```

### Integration with Development Workflow

**Team Configuration Example**
```javascript
// .claude/branch-checkin.config.js
module.exports = {
  complexity: {
    simple: { maxFiles: 5, fileTypes: ['.md', '.json'] },
    complex: { maxFiles: 25, requireOODA: ['src/core/', 'auth/'] },
    critical: { branches: ['main', 'release/*'], security: true }
  },
  quality: {
    coverage: { minimum: 85, trend: 'stable' },
    security: { maxSeverity: 'medium' },
    performance: { regressionThreshold: 10 }
  },
  team: {
    reviewers: { backend: '@backend-team', security: '@sec-team' },
    notifications: { slack: '#dev-updates' }
  }
};
```

**Learning Analytics Dashboard**
```bash
# Team OODA adoption metrics
OODA Methodology Analytics:
├── Usage Patterns (Last 30 Days)
│   ├── Simple scenarios: 245 (avg 8.2s execution)
│   ├── Complex scenarios: 67 (avg 3.1m execution)  
│   ├── Critical scenarios: 12 (avg 6.8m execution)
│   └── Manual OODA: 23 (learning/training usage)
├── Quality Improvements
│   ├── Issues prevented: 34 (vs 12 previous period)
│   ├── Test coverage: 91.3% (↑2.1% improvement)
│   ├── Security vulnerabilities: 3 (↓8 reduction)
│   └── Performance regressions: 1 (↓5 reduction)
├── Team Efficiency
│   ├── Total time saved: 12.4 hours (automation gains)
│   ├── Quality gate compliance: 97.3% (↑4.1%)
│   ├── Review cycle time: 1.2 days (↓0.6 reduction)
│   └── Production incidents: 0 (↓3 reduction)
└── Learning Progress
    ├── OODA comprehension: 8.7/10 team average
    ├── Methodology adoption: 89% active usage
    ├── Decision quality: Significant improvement
    └── Strategic thinking: Enhanced across team
```

This example demonstrates how OODA methodology can be embedded into development tools to provide adaptive intelligence that scales complexity handling while maintaining the precision and systematicness that military decision-making frameworks provide.

## Example 2: Legacy System Modernization

### Scenario
Modernizing a 10-year-old Node.js application with outdated dependencies, security vulnerabilities, and technical debt.

### OODA-Enhanced Workflow

#### Phase 1: Observe (Data Gathering)

**CLAUDE.md Setup**
```markdown
# Legacy Modernization Project Context

## Constraints
- Must maintain backward compatibility
- Zero downtime deployment required
- Budget: 200 development hours
- Timeline: 6 weeks

## Current System
- Node.js 12.x (EOL)
- Express 4.x with custom middleware
- MySQL 5.7 with complex stored procedures
- jQuery frontend with minimal testing

## Risk Factors
- Critical business operations depend on this system
- Limited documentation available
- Original developers no longer with company
```

**Systematic Observation with Claude**
```bash
# Use Claude as OODA Observe agent
claude_observe() {
    # Codebase structure analysis
    claude "Act as OODA Observe agent. Systematically analyze this legacy Node.js codebase:
    
    1. Map the complete application architecture
    2. Identify all dependencies and their versions
    3. Analyze security vulnerabilities using npm audit
    4. Document existing API endpoints and data flows
    5. Assess test coverage and quality
    6. Identify performance bottlenecks
    7. Map database schema and relationships
    8. Document business logic patterns
    
    Create a comprehensive observation report."
    
    # Save observation data
    claude "Create a structured observation report in JSON format for easy processing"
}
```

**Observable Outputs**
- Dependency vulnerability matrix
- Architecture visualization
- Code quality metrics
- Performance baseline measurements
- Risk assessment matrix

#### Phase 2: Orient (Strategic Analysis)

**Strategic Option Analysis**
```bash
claude_orient() {
    # Load observation data
    observation_data=$(cat observation_report.json)
    
    claude "Act as OODA Orient agent. Based on this observation data:
    
    $observation_data
    
    Analyze strategic modernization approaches:
    
    1. Big Bang Rewrite
       - Pros: Clean slate, modern architecture
       - Cons: High risk, long timeline, potential business disruption
       - Effort: 400+ hours
       - Risk: High
    
    2. Incremental Strangler Fig Pattern
       - Pros: Lower risk, continuous delivery, gradual migration
       - Cons: Temporary complexity, longer overall timeline
       - Effort: 250 hours
       - Risk: Medium
    
    3. Lift and Shift with Selective Modernization
       - Pros: Quick wins, targeted improvements
       - Cons: Technical debt remains, limited architectural improvements
       - Effort: 150 hours
       - Risk: Low
    
    Evaluate each approach against our constraints and provide strategic recommendations."
}
```

**Orientation Analysis Output**
```markdown
# Strategic Analysis Report

## Recommended Approach: Incremental Strangler Fig Pattern

### Rationale
- Aligns with zero-downtime requirement
- Fits within budget and timeline constraints
- Allows for continuous value delivery
- Reduces risk through incremental validation

### Implementation Strategy
1. **Phase 1**: Infrastructure modernization (Docker, CI/CD)
2. **Phase 2**: Security vulnerability fixes
3. **Phase 3**: API layer modernization with new endpoints
4. **Phase 4**: Frontend component migration
5. **Phase 5**: Database optimization and migration

### Success Metrics
- Zero production incidents during migration
- 50% reduction in security vulnerabilities within 4 weeks
- 30% performance improvement by project end
- 80% test coverage for new components
```

#### Phase 3: Decide (Implementation Planning)

**Decision Framework with Claude**
```bash
claude_decide() {
    orientation_analysis=$(cat strategic_analysis.md)
    
    claude "Act as OODA Decide agent. Based on this strategic analysis:
    
    $orientation_analysis
    
    Make specific implementation decisions:
    
    1. Choose the optimal technology stack for new components
    2. Define the migration sequence and dependencies
    3. Establish quality gates and rollback criteria
    4. Allocate resources and timeline for each phase
    5. Define success criteria and measurement methods
    
    Create a detailed implementation plan with:
    - Weekly milestones
    - Risk mitigation strategies
    - Quality assurance checkpoints
    - Rollback procedures
    
    Output format: Executable project plan with specific actions"
}
```

**Decision Output: Implementation Plan**
```yaml
# Modernization Implementation Plan

implementation_phases:
  phase_1_infrastructure:
    duration: "Week 1-2"
    effort: "40 hours"
    deliverables:
      - Dockerfile and docker-compose setup
      - GitHub Actions CI/CD pipeline
      - Staging environment deployment
      - Monitoring and logging setup
    success_criteria:
      - Automated deployment working
      - Zero manual deployment steps
      - Comprehensive logging in place
    
  phase_2_security:
    duration: "Week 2-3"  
    effort: "35 hours"
    deliverables:
      - All critical vulnerabilities fixed
      - Dependency updates (non-breaking)
      - Security headers implementation
      - Input validation improvements
    success_criteria:
      - Zero critical/high vulnerabilities
      - Security scan passing
      - No regression in functionality

technology_decisions:
  new_components:
    runtime: "Node.js 18 LTS"
    framework: "Express 4.18+ or Fastify"
    database: "MySQL 8.0 with connection pooling"
    testing: "Jest with supertest"
    frontend: "React 18 with TypeScript"
  
migration_sequence:
  1: "Authentication service"
  2: "User management API"  
  3: "Core business logic APIs"
  4: "Frontend components (page by page)"
  5: "Database optimization"

quality_gates:
  - "All tests passing"
  - "Code coverage > 80%"
  - "Performance regression < 10%"
  - "Security scan clean"
  - "Load test passing"

rollback_criteria:
  - "Response time increase > 20%"
  - "Error rate increase > 1%"
  - "Any critical functionality broken"
```

#### Phase 4: Act (Precise Implementation)

**OODA Act with Claude Code Excellence**
```bash
claude_act() {
    implementation_plan=$(cat implementation_plan.yaml)
    
    # Create custom slash command for implementation tracking
    cat > .claude/commands/implement-phase.md << 'EOF'
Implement modernization phase: $ARGUMENTS

Context: Legacy Node.js application modernization following OODA methodology
Implementation Plan: See implementation_plan.yaml

Steps:
1. Review phase requirements and deliverables
2. Set up development environment for this phase
3. Implement changes following established patterns
4. Run comprehensive tests (unit, integration, security)
5. Update documentation and deployment procedures
6. Execute quality gates validation
7. Prepare rollback procedures
8. Create deployment checklist
9. Execute deployment with monitoring
10. Validate success criteria and document results

Quality Requirements:
- Follow existing code style and patterns
- Maintain backward compatibility
- Ensure comprehensive error handling
- Include monitoring and logging
- Document all changes and decisions
EOF

    # Execute each phase with precision
    for phase in infrastructure security api_migration frontend_migration database_optimization; do
        claude "/implement-phase $phase"
        validate_phase_completion "$phase"
        create_phase_documentation "$phase"
    done
}

validate_phase_completion() {
    local phase=$1
    echo "Validating $phase completion..."
    
    # Run automated tests
    npm test
    npm run integration-test
    npm run security-scan
    
    # Check quality gates
    check_coverage_threshold
    check_performance_metrics
    check_security_requirements
    
    # Validate against success criteria
    validate_success_criteria "$phase"
}
```

**Act Phase Implementation Example: Security Phase**

```bash
# Phase 2: Security Implementation with Claude
claude "Implement Phase 2 security improvements:

Current vulnerabilities from npm audit:
$(npm audit --json)

Requirements:
1. Update all dependencies with critical/high vulnerabilities
2. Implement security headers middleware
3. Add input validation for all endpoints
4. Set up automated security scanning
5. Document security improvements

Follow these constraints:
- Test each dependency update individually
- Maintain backward compatibility
- Add comprehensive tests for new security features
- Document all changes in CHANGELOG.md

Create implementation plan and execute step-by-step."
```

**Claude's Security Implementation Response:**
```javascript
// security-middleware.js - Comprehensive security implementation
const helmet = require('helmet');
const rateLimit = require('express-rate-limit');
const validator = require('express-validator');

const securityMiddleware = {
  // Security headers
  headers: helmet({
    contentSecurityPolicy: {
      directives: {
        defaultSrc: ["'self'"],
        styleSrc: ["'self'", "'unsafe-inline'"],
        scriptSrc: ["'self'"],
        imgSrc: ["'self'", "data:", "https:"]
      }
    },
    hsts: {
      maxAge: 31536000,
      includeSubDomains: true,
      preload: true
    }
  }),

  // Rate limiting
  rateLimiter: rateLimit({
    windowMs: 15 * 60 * 1000, // 15 minutes
    max: 100, // limit each IP to 100 requests per windowMs
    message: 'Too many requests from this IP',
    standardHeaders: true,
    legacyHeaders: false
  }),

  // Input validation schemas
  validateUser: [
    validator.body('email').isEmail().normalizeEmail(),
    validator.body('password').isLength({ min: 8 }).isStrongPassword(),
    validator.body('name').isLength({ min: 2, max: 50 }).trim().escape()
  ],

  // Error handling middleware
  handleValidationErrors: (req, res, next) => {
    const errors = validator.validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({
        success: false,
        errors: errors.array()
      });
    }
    next();
  }
};

module.exports = securityMiddleware;
```

**Automated Quality Validation:**
```bash
# test/security.test.js - Comprehensive security tests
const request = require('supertest');
const app = require('../app');

describe('Security Implementation', () => {
  describe('Security Headers', () => {
    it('should set all required security headers', async () => {
      const response = await request(app).get('/');
      
      expect(response.headers['x-frame-options']).toBe('DENY');
      expect(response.headers['x-content-type-options']).toBe('nosniff');
      expect(response.headers['strict-transport-security']).toContain('max-age=31536000');
      expect(response.headers['content-security-policy']).toContain("default-src 'self'");
    });
  });

  describe('Rate Limiting', () => {
    it('should enforce rate limits', async () => {
      // Make 101 requests to exceed limit
      const requests = Array(101).fill().map(() => 
        request(app).get('/api/test')
      );
      
      const responses = await Promise.all(requests);
      const rateLimited = responses.filter(r => r.status === 429);
      
      expect(rateLimited.length).toBeGreaterThan(0);
    });
  });

  describe('Input Validation', () => {
    it('should validate and sanitize user input', async () => {
      const invalidUser = {
        email: 'invalid-email',
        password: '123',
        name: '<script>alert("xss")</script>'
      };
      
      const response = await request(app)
        .post('/api/users')
        .send(invalidUser);
      
      expect(response.status).toBe(400);
      expect(response.body.errors).toBeDefined();
      expect(response.body.errors.length).toBeGreaterThan(0);
    });
  });
});
```

## Example 2: API Development with OODA Methodology

### Scenario
Designing and implementing a new REST API for a microservices architecture with complex business requirements.

### OODA-Enhanced API Development

#### Observe: Requirements Analysis
```bash
# Use Claude for comprehensive requirements gathering
claude "Act as OODA Observe agent for API development:

Business Requirements:
- E-commerce order processing system
- Handle 10K+ orders per day
- Support multiple payment methods
- Integration with inventory, shipping, and notification services
- Real-time order status updates
- Compliance with PCI DSS standards

Technical Environment:
- Node.js with Express
- PostgreSQL database
- Redis for caching and sessions
- Docker containerization
- Kubernetes deployment
- Existing microservices: User, Inventory, Payment, Shipping

Analyze and document:
1. Complete API specification requirements
2. Integration points and dependencies
3. Performance and scalability requirements
4. Security and compliance requirements
5. Error handling and monitoring requirements
6. Testing and validation requirements

Generate a comprehensive API requirements document."
```

#### Orient: Architecture Design Options

```bash
claude "Act as OODA Orient agent. Based on the API requirements analysis:

$(cat api_requirements.md)

Evaluate these architectural approaches:

1. **Monolithic API Service**
   - Single service handling all order operations
   - Direct database connections
   - Synchronous service calls
   
2. **Event-Driven Microservice**
   - Order service publishes events
   - Asynchronous processing with message queues
   - Eventual consistency model
   
3. **API Gateway with Service Mesh**
   - Centralized API gateway
   - Service mesh for inter-service communication
   - Distributed tracing and monitoring

Analyze each approach for:
- Scalability characteristics
- Complexity and maintenance burden
- Performance implications
- Error handling and recovery
- Development and deployment complexity
- Cost implications

Provide strategic recommendation with detailed justification."
```

#### Decide: Implementation Strategy

```bash
claude "Act as OODA Decide agent. Choose optimal implementation strategy:

Strategic Analysis: $(cat architecture_analysis.md)

Make specific decisions for:

1. **API Architecture**: Event-driven microservice with CQRS
2. **Technology Stack**: 
   - Framework: Fastify (performance optimized)
   - Database: PostgreSQL with read replicas
   - Message Queue: Redis Streams
   - Caching: Redis with intelligent invalidation
   - Monitoring: OpenTelemetry + Prometheus

3. **Implementation Phases**:
   - Phase 1: Core order CRUD operations
   - Phase 2: Payment integration and processing
   - Phase 3: Inventory synchronization
   - Phase 4: Real-time status updates
   - Phase 5: Performance optimization

4. **Quality Gates**:
   - API response time < 200ms (95th percentile)
   - Throughput > 1000 RPS
   - 99.9% uptime SLA
   - Zero data consistency issues
   - Comprehensive error handling

Create detailed implementation plan with milestones and success criteria."
```

#### Act: Precision Implementation

**Custom CLAUDE.md for API Development**
```markdown
# Order API Development Context

## Architecture Decisions
- Event-driven microservice with CQRS pattern
- Fastify framework for high performance
- PostgreSQL with read replicas for scalability
- Redis Streams for reliable message processing

## Development Standards
- OpenAPI 3.0 specification driven development
- Test-driven development with >90% coverage
- Contract testing with consumer services
- Comprehensive error handling with structured logging
- Performance monitoring with APM integration

## Quality Requirements
- All endpoints must have comprehensive OpenAPI documentation
- Every endpoint must have unit, integration, and contract tests
- Error responses must follow RFC 7807 problem details format
- All operations must be observable with distributed tracing
- Security headers and input validation required

## Integration Patterns
- Use Redis Streams for event publishing
- Implement circuit breaker pattern for external service calls
- Use optimistic locking for concurrent operations
- Implement idempotency for all state-changing operations
```

**Implementation with Claude Code**
```bash
# Create custom slash command for API development
cat > .claude/commands/api-endpoint.md << 'EOF'
Create API endpoint: $ARGUMENTS

Follow our API development standards:

1. Create OpenAPI specification first
2. Implement endpoint with comprehensive error handling
3. Add input validation and sanitization
4. Implement business logic with proper separation of concerns
5. Add comprehensive tests (unit, integration, contract)
6. Add monitoring and observability
7. Update documentation and examples
8. Verify performance meets SLA requirements

Requirements:
- Follow CQRS pattern where applicable
- Use proper HTTP status codes
- Implement idempotency for POST/PUT operations
- Add comprehensive logging
- Include security considerations
- Follow existing code patterns and style
EOF

# Implement Order Creation endpoint
claude "/api-endpoint POST /orders - Create new order with payment processing"
```

**Claude's Comprehensive Implementation:**

```javascript
// routes/orders.js - Order creation with OODA precision
const fastify = require('fastify');
const { OrderService } = require('../services/OrderService');
const { ValidationSchemas } = require('../schemas/OrderSchemas');
const { ErrorHandler } = require('../utils/ErrorHandler');
const { Logger } = require('../utils/Logger');
const { Metrics } = require('../monitoring/Metrics');

/**
 * OpenAPI specification for order creation
 */
const createOrderSchema = {
  description: 'Create a new order with payment processing',
  tags: ['orders'],
  body: ValidationSchemas.createOrder,
  response: {
    201: ValidationSchemas.orderResponse,
    400: ValidationSchemas.errorResponse,
    409: ValidationSchemas.conflictResponse,
    500: ValidationSchemas.errorResponse
  },
  security: [{ apiKey: [] }]
};

async function orderRoutes(fastify, options) {
  const orderService = new OrderService({
    database: options.database,
    eventPublisher: options.eventPublisher,
    logger: options.logger
  });

  // POST /orders - Create new order
  fastify.post('/orders', {
    schema: createOrderSchema,
    preHandler: [
      fastify.authenticate, // Authentication middleware
      fastify.rateLimit({ max: 100, timeWindow: '1 minute' }), // Rate limiting
      fastify.validateIdempotencyKey // Idempotency validation
    ]
  }, async (request, reply) => {
    const startTime = process.hrtime.bigint();
    const traceId = request.headers['x-trace-id'] || generateTraceId();
    
    try {
      // Structured logging with trace ID
      Logger.info('Order creation started', {
        traceId,
        userId: request.user.id,
        orderData: sanitizeOrderData(request.body)
      });

      // Input validation and sanitization
      const validatedOrder = await validateAndSanitizeOrder(request.body);
      
      // Business logic execution with proper error handling
      const order = await orderService.createOrder({
        ...validatedOrder,
        userId: request.user.id,
        idempotencyKey: request.headers['idempotency-key'],
        traceId
      });

      // Event publishing for downstream services
      await orderService.publishOrderCreatedEvent(order, traceId);

      // Performance monitoring
      const processingTime = Number(process.hrtime.bigint() - startTime) / 1000000;
      Metrics.histogram('order_creation_duration', processingTime);
      Metrics.increment('orders_created_total');

      Logger.info('Order created successfully', {
        traceId,
        orderId: order.id,
        processingTime
      });

      // Return response with proper status and headers
      return reply
        .code(201)
        .header('Location', `/orders/${order.id}`)
        .header('X-Trace-ID', traceId)
        .send({
          success: true,
          data: order,
          meta: {
            traceId,
            processingTime: `${processingTime}ms`
          }
        });

    } catch (error) {
      // Comprehensive error handling
      const processingTime = Number(process.hrtime.bigint() - startTime) / 1000000;
      
      Logger.error('Order creation failed', {
        traceId,
        error: error.message,
        stack: error.stack,
        processingTime,
        userId: request.user?.id
      });

      Metrics.increment('order_creation_errors_total', {
        error_type: error.code || 'unknown'
      });

      // Return structured error response (RFC 7807)
      return ErrorHandler.handleError(error, reply, traceId);
    }
  });

  // GET /orders/:id - Get order details  
  fastify.get('/orders/:id', {
    schema: {
      description: 'Get order details by ID',
      tags: ['orders'],
      params: ValidationSchemas.orderParams,
      response: {
        200: ValidationSchemas.orderResponse,
        404: ValidationSchemas.notFoundResponse,
        403: ValidationSchemas.forbiddenResponse
      }
    },
    preHandler: [fastify.authenticate]
  }, async (request, reply) => {
    // Implementation following same patterns...
  });
}

module.exports = orderRoutes;
```

**Comprehensive Testing Suite:**
```javascript
// test/routes/orders.test.js - Complete test coverage
const { test } = require('tap');
const { build } = require('../helper');
const { DatabaseHelper } = require('../helpers/DatabaseHelper');
const { MockServices } = require('../helpers/MockServices');

test('Order API Endpoints', async (t) => {
  const app = await build(t);
  
  t.beforeEach(async () => {
    await DatabaseHelper.resetTestData();
    MockServices.reset();
  });

  t.test('POST /orders', async (t) => {
    t.test('should create order successfully', async (t) => {
      const orderData = {
        items: [
          { productId: 'prod-123', quantity: 2, price: 29.99 }
        ],
        shippingAddress: {
          street: '123 Test St',
          city: 'TestCity',
          state: 'TS',
          zipCode: '12345'
        },
        paymentMethod: 'credit_card'
      };

      const response = await app.inject({
        method: 'POST',
        url: '/orders',
        headers: {
          'authorization': 'Bearer valid-token',
          'idempotency-key': 'test-key-123',
          'content-type': 'application/json'
        },
        payload: orderData
      });

      t.equal(response.statusCode, 201);
      t.ok(response.headers.location);
      t.ok(response.headers['x-trace-id']);
      
      const body = JSON.parse(response.body);
      t.equal(body.success, true);
      t.ok(body.data.id);
      t.ok(body.data.orderNumber);
      t.equal(body.data.status, 'pending');
      t.ok(body.meta.traceId);
    });

    t.test('should handle validation errors', async (t) => {
      const invalidData = {
        items: [], // Empty items should fail validation
        shippingAddress: {} // Missing required fields
      };

      const response = await app.inject({
        method: 'POST',
        url: '/orders',
        headers: {
          'authorization': 'Bearer valid-token',
          'content-type': 'application/json'
        },
        payload: invalidData
      });

      t.equal(response.statusCode, 400);
      const body = JSON.parse(response.body);
      t.equal(body.type, 'https://example.com/problems/validation-error');
      t.ok(body.detail);
      t.ok(Array.isArray(body.errors));
    });

    t.test('should handle idempotency', async (t) => {
      const orderData = {
        items: [{ productId: 'prod-123', quantity: 1, price: 19.99 }],
        shippingAddress: { street: '123 Test St', city: 'TestCity', state: 'TS', zipCode: '12345' },
        paymentMethod: 'credit_card'
      };

      // First request
      const response1 = await app.inject({
        method: 'POST',
        url: '/orders',
        headers: {
          'authorization': 'Bearer valid-token',
          'idempotency-key': 'duplicate-key',
          'content-type': 'application/json'
        },
        payload: orderData
      });

      // Second request with same idempotency key
      const response2 = await app.inject({
        method: 'POST',
        url: '/orders',
        headers: {
          'authorization': 'Bearer valid-token',
          'idempotency-key': 'duplicate-key',
          'content-type': 'application/json'
        },
        payload: orderData
      });

      t.equal(response1.statusCode, 201);
      t.equal(response2.statusCode, 200); // Idempotent response
      
      const body1 = JSON.parse(response1.body);
      const body2 = JSON.parse(response2.body);
      t.equal(body1.data.id, body2.data.id); // Same order returned
    });

    t.test('should handle rate limiting', async (t) => {
      const promises = Array(102).fill().map((_, i) => 
        app.inject({
          method: 'POST',
          url: '/orders',
          headers: {
            'authorization': 'Bearer valid-token',
            'idempotency-key': `test-key-${i}`,
            'content-type': 'application/json'
          },
          payload: { items: [{ productId: 'prod-123', quantity: 1, price: 9.99 }] }
        })
      );

      const responses = await Promise.all(promises);
      const rateLimited = responses.filter(r => r.statusCode === 429);
      t.ok(rateLimited.length > 0, 'Should have rate limited requests');
    });
  });

  t.test('Performance Requirements', async (t) => {
    t.test('should meet response time SLA', async (t) => {
      const startTime = process.hrtime.bigint();
      
      await app.inject({
        method: 'POST',
        url: '/orders',
        headers: {
          'authorization': 'Bearer valid-token',
          'idempotency-key': 'perf-test',
          'content-type': 'application/json'
        },
        payload: {
          items: [{ productId: 'prod-123', quantity: 1, price: 19.99 }],
          shippingAddress: { street: '123 Test St', city: 'TestCity', state: 'TS', zipCode: '12345' },
          paymentMethod: 'credit_card'
        }
      });

      const endTime = process.hrtime.bigint();
      const responseTime = Number(endTime - startTime) / 1000000; // Convert to ms
      
      t.ok(responseTime < 200, `Response time ${responseTime}ms should be < 200ms`);
    });
  });
});
```

## Example 3: Frontend Development with OODA

### Scenario
Building a complex React dashboard with real-time data visualization and user interaction requirements.

### OODA-Enhanced Frontend Development

#### Observe: User Experience Analysis

```bash
# Use Claude for comprehensive UX observation
claude "Act as OODA Observe agent for dashboard development:

User Requirements:
- Real-time financial trading dashboard
- Display multiple asset classes and markets  
- Support 1000+ concurrent users
- Mobile-responsive design
- Accessibility compliance (WCAG 2.1 AA)
- Sub-second data updates
- Complex charting and visualization

Current Environment:
- React 18 with TypeScript
- Material-UI component library
- WebSocket for real-time data
- Redux Toolkit for state management
- React Query for server state
- Vite build system

Analyze and document:
1. User interaction patterns and workflows
2. Performance requirements and constraints  
3. Data flow and state management needs
4. Accessibility and usability requirements
5. Cross-browser compatibility needs
6. Mobile responsiveness considerations
7. Real-time data synchronization challenges

Generate comprehensive UX analysis and technical requirements."
```

#### Orient: Architecture and Design Strategy

**Strategic Analysis with Claude**
```bash
claude "Act as OODA Orient agent. Analyze frontend architecture options:

UX Requirements: $(cat dashboard_ux_analysis.md)

Evaluate these architectural approaches:

1. **Monolithic SPA with Global State**
   - Single Redux store for all application state
   - Component tree with prop drilling
   - Centralized data fetching

2. **Micro-Frontend Architecture**  
   - Independent React applications per domain
   - Module federation for code sharing
   - Separate state management per micro-app

3. **Component-Based Architecture with Atomic Design**
   - Atomic design principles (atoms, molecules, organisms)
   - Context-based state management
   - Server state separation with React Query

Analyze for:
- Development team scalability
- Performance characteristics  
- Code maintainability
- Testing complexity
- Deployment flexibility
- User experience consistency

Recommend optimal architecture with implementation strategy."
```

#### Decide: Implementation Plan

```bash
claude "Act as OODA Decide agent. Create implementation plan:

Architecture Analysis: $(cat frontend_architecture_analysis.md)

Make specific decisions:

1. **Architecture**: Component-based with Atomic Design + Context API
2. **State Management Strategy**:
   - Server State: React Query with optimistic updates
   - Client State: Context API with useReducer
   - Real-time Data: Custom WebSocket hook with reconnection

3. **Development Approach**:
   - Storybook for component development
   - Test-driven development with React Testing Library
   - Performance monitoring with Web Vitals
   - Accessibility testing with axe-core

4. **Implementation Phases**:
   - Phase 1: Design system and core components
   - Phase 2: Data layer and WebSocket integration
   - Phase 3: Dashboard layout and navigation
   - Phase 4: Chart components and visualizations
   - Phase 5: Real-time features and optimization

Create detailed sprint plan with component specifications."
```

#### Act: Precision Frontend Implementation

**Custom CLAUDE.md for Frontend Development**
```markdown
# Trading Dashboard Development Context

## Architecture Decisions
- Atomic Design with TypeScript
- Context API for client state, React Query for server state
- Custom WebSocket hooks for real-time data
- Storybook-driven component development
- Performance-first approach with Web Vitals monitoring

## Development Standards  
- All components must have TypeScript interfaces
- 100% component test coverage required
- Storybook stories for all UI components
- Accessibility testing with automated axe checks
- Performance budgets: LCP < 2.5s, FID < 100ms, CLS < 0.1
- Mobile-first responsive design

## Code Style
- Use React hooks and functional components exclusively
- Implement proper error boundaries
- Use React.memo for expensive components
- Implement proper loading and error states
- Follow Material Design guidelines with custom theme

## Real-time Data Patterns
- WebSocket connection with automatic reconnection
- Optimistic updates for better UX
- Data normalization for efficient updates
- Proper cleanup in useEffect hooks
```

**Implementation with Claude Code**
```bash
# Create specialized slash command for React components
cat > .claude/commands/react-component.md << 'EOF'
Create React component: $ARGUMENTS

Follow our frontend development standards:

1. Create TypeScript interface definitions
2. Implement component with proper props typing
3. Add comprehensive error handling and loading states
4. Implement accessibility features (ARIA labels, keyboard navigation)
5. Create Storybook stories with all variants
6. Add comprehensive tests with React Testing Library
7. Implement responsive design with Mobile-first approach
8. Add performance optimizations (memoization, lazy loading)
9. Document component usage and examples

Quality Requirements:
- TypeScript strict mode compliance
- 100% test coverage
- Accessibility compliance (WCAG 2.1 AA)
- Performance optimized (React.memo where appropriate)
- Responsive design validation
- Error boundary integration
EOF

# Implement real-time trading chart component
claude "/react-component TradingChart - Real-time candlestick chart with WebSocket data"
```

**Claude's Comprehensive Component Implementation:**

```typescript
// components/TradingChart/TradingChart.tsx
import React, { memo, useCallback, useEffect, useMemo, useRef, useState } from 'react';
import { Box, CircularProgress, Alert, useTheme } from '@mui/material';
import { Chart, ChartConfiguration } from 'chart.js/auto';
import { useWebSocket } from '../../hooks/useWebSocket';
import { useErrorBoundary } from '../../hooks/useErrorBoundary';
import { CandlestickData, TradingSymbol } from '../../types/trading.types';

// TypeScript interfaces
export interface TradingChartProps {
  /** Trading symbol to display (e.g., 'BTCUSD', 'ETHUSD') */
  symbol: TradingSymbol;
  /** Chart height in pixels */
  height?: number;
  /** Time interval for candlesticks */
  interval?: '1m' | '5m' | '15m' | '1h' | '4h' | '1d';
  /** Enable/disable real-time updates */
  realTime?: boolean;
  /** Callback when chart data changes */
  onDataChange?: (data: CandlestickData[]) => void;
  /** ARIA label for accessibility */
  ariaLabel?: string;
  /** Custom theme overrides */
  themeOverrides?: Partial<ChartConfiguration>;
}

interface ChartState {
  isLoading: boolean;
  error: string | null;
  data: CandlestickData[];
  lastUpdate: Date | null;
}

/**
 * TradingChart - Real-time candlestick chart component
 * 
 * Features:
 * - Real-time WebSocket data updates
 * - Responsive design with touch support
 * - Accessibility compliant
 * - Performance optimized with memoization
 * - Comprehensive error handling
 * 
 * @example
 * ```tsx
 * <TradingChart 
 *   symbol="BTCUSD" 
 *   interval="5m"
 *   realTime={true}
 *   onDataChange={(data) => console.log('New data:', data)}
 * />
 * ```
 */
export const TradingChart = memo<TradingChartProps>(({
  symbol,
  height = 400,
  interval = '5m',
  realTime = true,
  onDataChange,
  ariaLabel,
  themeOverrides
}) => {
  const theme = useTheme();
  const canvasRef = useRef<HTMLCanvasElement>(null);
  const chartRef = useRef<Chart | null>(null);
  const { showBoundary } = useErrorBoundary();
  
  const [chartState, setChartState] = useState<ChartState>({
    isLoading: true,
    error: null,
    data: [],
    lastUpdate: null
  });

  // WebSocket connection for real-time data
  const { data: wsData, isConnected, error: wsError } = useWebSocket({
    url: `wss://api.trading.com/ws/v1/candlesticks/${symbol}/${interval}`,
    enabled: realTime,
    onMessage: useCallback((data: CandlestickData) => {
      setChartState(prev => {
        const newData = [...prev.data];
        const existingIndex = newData.findIndex(item => item.timestamp === data.timestamp);
        
        if (existingIndex >= 0) {
          // Update existing candlestick
          newData[existingIndex] = data;
        } else {
          // Add new candlestick
          newData.push(data);
          // Keep last 200 candlesticks for performance
          if (newData.length > 200) {
            newData.shift();
          }
        }
        
        return {
          ...prev,
          data: newData,
          lastUpdate: new Date(),
          isLoading: false
        };
      });
    }, []),
    onError: useCallback((error: Error) => {
      setChartState(prev => ({
        ...prev,
        error: error.message,
        isLoading: false
      }));
    }, [])
  });

  // Chart configuration with theme integration
  const chartConfig = useMemo<ChartConfiguration>(() => ({
    type: 'candlestick',
    data: {
      datasets: [{
        label: `${symbol} Candlesticks`,
        data: chartState.data,
        borderColor: theme.palette.primary.main,
        backgroundColor: theme.palette.primary.light,
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      interaction: {
        intersect: false,
        mode: 'index'
      },
      scales: {
        x: {
          type: 'time',
          time: {
            unit: interval.includes('m') ? 'minute' : 'hour'
          },
          grid: {
            color: theme.palette.divider
          }
        },
        y: {
          beginAtZero: false,
          grid: {
            color: theme.palette.divider
          }
        }
      },
      plugins: {
        legend: {
          display: true,
          labels: {
            color: theme.palette.text.primary
          }
        },
        tooltip: {
          backgroundColor: theme.palette.background.paper,
          titleColor: theme.palette.text.primary,
          bodyColor: theme.palette.text.secondary,
          borderColor: theme.palette.divider,
          borderWidth: 1
        }
      },
      // Custom theme overrides
      ...themeOverrides
    },
    plugins: [{
      id: 'accessibility',
      afterDraw: (chart) => {
        // Add ARIA live region updates for screen readers
        const announcement = `Chart updated with ${chartState.data.length} data points. Latest price: ${chartState.data[chartState.data.length - 1]?.close || 'N/A'}`;
        announceToScreenReader(announcement);
      }
    }]
  }), [symbol, interval, theme, chartState.data, themeOverrides]);

  // Initialize and update chart
  useEffect(() => {
    if (!canvasRef.current) return;

    try {
      // Destroy existing chart
      if (chartRef.current) {
        chartRef.current.destroy();
      }

      // Create new chart
      chartRef.current = new Chart(canvasRef.current, chartConfig);
    } catch (error) {
      showBoundary(error);
    }

    return () => {
      if (chartRef.current) {
        chartRef.current.destroy();
        chartRef.current = null;
      }
    };
  }, [chartConfig, showBoundary]);

  // Update chart data
  useEffect(() => {
    if (chartRef.current && chartState.data.length > 0) {
      chartRef.current.data.datasets[0].data = chartState.data;
      chartRef.current.update('none'); // Performance optimized update
    }
  }, [chartState.data]);

  // Callback for data changes
  useEffect(() => {
    if (onDataChange && chartState.data.length > 0) {
      onDataChange(chartState.data);
    }
  }, [chartState.data, onDataChange]);

  // Error handling
  if (chartState.error || wsError) {
    return (
      <Alert 
        severity="error" 
        aria-live="polite"
        role="alert"
      >
        Failed to load chart data: {chartState.error || wsError}
      </Alert>
    );
  }

  // Loading state
  if (chartState.isLoading) {
    return (
      <Box 
        display="flex" 
        justifyContent="center" 
        alignItems="center" 
        height={height}
        role="progressbar"
        aria-label="Loading chart data"
      >
        <CircularProgress />
      </Box>
    );
  }

  return (
    <Box 
      position="relative" 
      height={height}
      role="img"
      aria-label={ariaLabel || `${symbol} candlestick chart showing ${interval} intervals`}
      aria-live="polite"
    >
      <canvas 
        ref={canvasRef}
        role="img"
        aria-describedby={`chart-description-${symbol}`}
        style={{ 
          width: '100%', 
          height: '100%',
          // Ensure proper focus indicators for keyboard navigation
          outline: 'none',
          border: theme.palette.mode === 'dark' ? '1px solid #444' : '1px solid #ddd'
        }}
        onFocus={(e) => {
          e.target.style.boxShadow = `0 0 0 2px ${theme.palette.primary.main}`;
        }}
        onBlur={(e) => {
          e.target.style.boxShadow = 'none';
        }}
        tabIndex={0}
      />
      
      {/* Screen reader description */}
      <div 
        id={`chart-description-${symbol}`} 
        className="sr-only"
        aria-live="polite"
      >
        {`Trading chart for ${symbol} with ${chartState.data.length} data points. 
         Connection status: ${isConnected ? 'Connected' : 'Disconnected'}. 
         Last updated: ${chartState.lastUpdate?.toLocaleTimeString() || 'Never'}`}
      </div>
    </Box>
  );
});

TradingChart.displayName = 'TradingChart';

// Utility function for screen reader announcements
function announceToScreenReader(message: string) {
  const announcement = document.createElement('div');
  announcement.setAttribute('aria-live', 'polite');
  announcement.setAttribute('aria-atomic', 'true');
  announcement.className = 'sr-only';
  announcement.textContent = message;
  
  document.body.appendChild(announcement);
  
  setTimeout(() => {
    document.body.removeChild(announcement);
  }, 1000);
}

export default TradingChart;
```

**Comprehensive Storybook Stories:**
```typescript
// components/TradingChart/TradingChart.stories.tsx
import type { Meta, StoryObj } from '@storybook/react';
import { action } from '@storybook/addon-actions';
import { ThemeProvider, createTheme } from '@mui/material/styles';
import { TradingChart } from './TradingChart';
import { mockCandlestickData } from '../../__mocks__/trading.mocks';

const meta: Meta<typeof TradingChart> = {
  title: 'Trading/TradingChart',
  component: TradingChart,
  parameters: {
    layout: 'centered',
    docs: {
      description: {
        component: 'Real-time trading chart component with WebSocket integration and full accessibility support.'
      }
    }
  },
  argTypes: {
    symbol: {
      control: { type: 'select' },
      options: ['BTCUSD', 'ETHUSD', 'AAPL', 'GOOGL']
    },
    interval: {
      control: { type: 'select' },
      options: ['1m', '5m', '15m', '1h', '4h', '1d']
    },
    height: {
      control: { type: 'range', min: 200, max: 800, step: 50 }
    },
    realTime: {
      control: { type: 'boolean' }
    }
  },
  decorators: [
    (Story) => (
      <ThemeProvider theme={createTheme()}>
        <div style={{ width: '800px', padding: '20px' }}>
          <Story />
        </div>
      </ThemeProvider>
    )
  ]
};

export default meta;
type Story = StoryObj<typeof meta>;

export const Default: Story = {
  args: {
    symbol: 'BTCUSD',
    interval: '5m',
    height: 400,
    realTime: false,
    onDataChange: action('onDataChange')
  }
};

export const Loading: Story = {
  args: {
    ...Default.args,
    // Mock loading state
  },
  parameters: {
    mockData: {
      loading: true
    }
  }
};

export const Error: Story = {
  args: {
    ...Default.args,
  },
  parameters: {
    mockData: {
      error: 'Failed to connect to WebSocket'
    }
  }
};

export const DifferentIntervals: Story = {
  render: () => (
    <div style={{ display: 'grid', gap: '20px' }}>
      <TradingChart symbol="BTCUSD" interval="1m" height={200} />
      <TradingChart symbol="BTCUSD" interval="5m" height={200} />
      <TradingChart symbol="BTCUSD" interval="1h" height={200} />
    </div>
  )
};

export const DarkTheme: Story = {
  args: {
    ...Default.args,
  },
  decorators: [
    (Story) => (
      <ThemeProvider theme={createTheme({ palette: { mode: 'dark' } })}>
        <div style={{ width: '800px', padding: '20px', backgroundColor: '#121212' }}>
          <Story />
        </div>
      </ThemeProvider>
    )
  ]
};

export const AccessibilityTest: Story = {
  args: {
    ...Default.args,
    ariaLabel: 'Bitcoin to USD trading chart with 5-minute intervals'
  },
  parameters: {
    a11y: {
      config: {
        rules: [
          {
            id: 'color-contrast',
            enabled: true
          }
        ]
      }
    }
  }
};
```

**Comprehensive Testing Suite:**
```typescript
// components/TradingChart/TradingChart.test.tsx
import { render, screen, waitFor, fireEvent } from '@testing-library/react';
import { ThemeProvider, createTheme } from '@mui/material/styles';
import { TradingChart } from './TradingChart';
import { mockWebSocket } from '../../__mocks__/websocket.mock';
import { mockCandlestickData } from '../../__mocks__/trading.mocks';

// Mock Chart.js
jest.mock('chart.js/auto', () => ({
  Chart: jest.fn().mockImplementation(() => ({
    destroy: jest.fn(),
    update: jest.fn(),
    data: { datasets: [{ data: [] }] }
  }))
}));

const renderWithTheme = (component: React.ReactElement) => {
  return render(
    <ThemeProvider theme={createTheme()}>
      {component}
    </ThemeProvider>
  );
};

describe('TradingChart', () => {
  beforeEach(() => {
    jest.clearAllMocks();
    mockWebSocket.mockClear();
  });

  describe('Component Rendering', () => {
    it('renders loading state initially', () => {
      renderWithTheme(<TradingChart symbol="BTCUSD" />);
      
      expect(screen.getByRole('progressbar')).toBeInTheDocument();
      expect(screen.getByLabelText('Loading chart data')).toBeInTheDocument();
    });

    it('renders chart after data loads', async () => {
      mockWebSocket.mockImplementation(() => ({
        data: mockCandlestickData,
        isConnected: true,
        error: null
      }));

      renderWithTheme(<TradingChart symbol="BTCUSD" />);

      await waitFor(() => {
        expect(screen.getByRole('img')).toBeInTheDocument();
      });
    });

    it('renders error state when WebSocket fails', async () => {
      mockWebSocket.mockImplementation(() => ({
        data: null,
        isConnected: false,
        error: 'Connection failed'
      }));

      renderWithTheme(<TradingChart symbol="BTCUSD" />);

      await waitFor(() => {
        expect(screen.getByRole('alert')).toBeInTheDocument();
        expect(screen.getByText(/Failed to load chart data/)).toBeInTheDocument();
      });
    });
  });

  describe('Accessibility', () => {
    it('has proper ARIA labels', async () => {
      renderWithTheme(
        <TradingChart 
          symbol="BTCUSD" 
          ariaLabel="Custom chart label"
        />
      );

      await waitFor(() => {
        const chart = screen.getByLabelText('Custom chart label');
        expect(chart).toBeInTheDocument();
      });
    });

    it('provides screen reader announcements', async () => {
      renderWithTheme(<TradingChart symbol="BTCUSD" />);

      await waitFor(() => {
        const description = screen.getByText(/Trading chart for BTCUSD/);
        expect(description).toBeInTheDocument();
      });
    });

    it('supports keyboard navigation', async () => {
      renderWithTheme(<TradingChart symbol="BTCUSD" />);

      await waitFor(() => {
        const canvas = screen.getByRole('img');
        expect(canvas).toHaveAttribute('tabIndex', '0');
        
        fireEvent.focus(canvas);
        expect(canvas).toHaveFocus();
      });
    });
  });

  describe('Real-time Updates', () => {
    it('updates chart when new data arrives', async () => {
      const onDataChange = jest.fn();
      
      renderWithTheme(
        <TradingChart 
          symbol="BTCUSD"
          realTime={true}
          onDataChange={onDataChange}
        />
      );

      // Simulate WebSocket data
      const newData = {
        timestamp: Date.now(),
        open: 45000,
        high: 45100,
        low: 44900,
        close: 45050,
        volume: 1000
      };

      mockWebSocket.simulateMessage(newData);

      await waitFor(() => {
        expect(onDataChange).toHaveBeenCalledWith(
          expect.arrayContaining([
            expect.objectContaining(newData)
          ])
        );
      });
    });

    it('handles WebSocket disconnection gracefully', async () => {
      renderWithTheme(<TradingChart symbol="BTCUSD" realTime={true} />);

      mockWebSocket.simulateDisconnection();

      await waitFor(() => {
        const status = screen.getByText(/Connection status: Disconnected/);
        expect(status).toBeInTheDocument();
      });
    });
  });

  describe('Performance', () => {
    it('limits data points for performance', async () => {
      const onDataChange = jest.fn();
      
      renderWithTheme(
        <TradingChart 
          symbol="BTCUSD"
          onDataChange={onDataChange}
        />
      );

      // Simulate 250 data points (should limit to 200)
      for (let i = 0; i < 250; i++) {
        mockWebSocket.simulateMessage({
          timestamp: Date.now() + i * 1000,
          open: 45000 + i,
          high: 45100 + i,
          low: 44900 + i,
          close: 45050 + i,
          volume: 1000
        });
      }

      await waitFor(() => {
        const lastCall = onDataChange.mock.calls[onDataChange.mock.calls.length - 1];
        expect(lastCall[0]).toHaveLength(200);
      });
    });

    it('uses performance optimized chart updates', async () => {
      const { Chart } = require('chart.js/auto');
      
      renderWithTheme(<TradingChart symbol="BTCUSD" />);
      
      mockWebSocket.simulateMessage(mockCandlestickData[0]);

      await waitFor(() => {
        expect(Chart.mock.instances[0].update).toHaveBeenCalledWith('none');
      });
    });
  });

  describe('Responsive Design', () => {
    it('adjusts to container size', () => {
      renderWithTheme(
        <div style={{ width: '500px' }}>
          <TradingChart symbol="BTCUSD" height={300} />
        </div>
      );

      const container = screen.getByRole('img').parentElement;
      expect(container).toHaveStyle({ height: '300px' });
    });
  });
});
```

This comprehensive OODA + Claude Code integration demonstrates how systematic decision-making enhances development outcomes through:

1. **Observe**: Comprehensive requirements gathering and environmental analysis
2. **Orient**: Strategic evaluation of architectural options with trade-off analysis  
3. **Decide**: Data-driven selection of optimal approaches with clear success criteria
4. **Act**: Precision implementation with built-in quality assurance and validation

The examples show how Claude Code's capabilities are amplified when guided by OODA methodology, resulting in higher-quality, more maintainable, and better-validated software solutions.