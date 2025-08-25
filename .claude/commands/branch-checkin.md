Execute GitHub branch check-in workflow: $ARGUMENTS

This command implements an adaptive intelligence approach to branch check-in, with selective OODA integration for complex scenarios.

**Command Usage:**
- `/branch-checkin` - Smart check-in with automatic branch detection
- `/branch-checkin "commit message"` - Check-in with custom commit message  
- `/branch-checkin branch-name "commit message"` - Check-in to specific branch
- `/branch-checkin --ooda` - Force OODA methodology for complex scenarios
- `/branch-checkin --push` - Include push to remote repository

**Adaptive Intelligence Workflow:**

## Phase 1: Smart Assessment (Observe)
1. **Automatic Context Detection:**
   - Analyze current git status and working directory changes
   - Identify complexity indicators (files changed, merge conflicts, new dependencies)
   - Detect branch type (feature, hotfix, release) from naming patterns
   - Assess repository health (tests, linting, security vulnerabilities)

2. **Intelligence Triggers:**
   - Simple scenario: <10 files, no conflicts, passing tests → Direct execution
   - Complex scenario: >10 files, conflicts, failing tests, security issues → OODA activation
   - Critical scenario: Production branches, breaking changes → Full OODA with validation

## Phase 2: Strategic Analysis (Orient) - Activated for Complex Scenarios
3. **Risk Assessment Matrix:**
   - Evaluate potential impact of changes on codebase
   - Identify dependencies and integration points
   - Analyze test coverage and quality implications
   - Review security and compliance requirements

4. **Strategy Formulation:**
   - Determine optimal commit strategy (atomic, squashed, or multi-commit)
   - Plan testing and validation sequence
   - Identify rollback procedures and safety nets
   - Select appropriate branch protection and review requirements

## Phase 3: Decision Framework (Decide) - For High-Risk Scenarios
5. **Execution Planning:**
   - Choose commit message format following conventional commits
   - Select testing strategy (unit, integration, end-to-end)
   - Determine PR requirements and review assignments
   - Plan deployment and monitoring approach

## Phase 4: Precision Execution (Act) - All Scenarios
6. **Pre-commit Validation:**
   - Run automated tests and linting checks
   - Perform security vulnerability scanning
   - Validate code formatting and style compliance
   - Check for sensitive data or credentials

7. **Intelligent Commit Process:**
   - Stage files with smart selection (exclude generated files, logs)
   - Generate semantic commit messages with AI assistance
   - Create atomic commits for logical changes
   - Add co-authored-by tags when applicable

8. **Branch Management:**
   - Update branch with latest remote changes if needed
   - Handle merge conflicts with intelligent resolution suggestions
   - Ensure branch is up-to-date with base branch
   - Apply branch naming conventions and policies

9. **Quality Gates:**
   - Verify all tests pass before commit
   - Confirm no linting or type-checking errors
   - Validate performance metrics within acceptable thresholds
   - Ensure documentation is updated for significant changes

10. **GitHub Integration:**
    - Push changes to remote repository (if --push flag used)
    - Create or update pull request with comprehensive description
    - Apply appropriate labels and assign reviewers
    - Link related issues and set milestones
    - Add automated checks and required reviews

11. **Monitoring and Feedback:**
    - Set up branch protection rules if needed
    - Monitor CI/CD pipeline status
    - Track code coverage and quality metrics
    - Provide clear success feedback and next steps

**Error Handling and Recovery:**
- Automatic stashing of work in progress before operations
- Intelligent conflict resolution with user guidance
- Rollback procedures for failed operations
- Clear error messages with actionable next steps
- Preservation of work and prevention of data loss

**Integration Points:**
- GitHub CLI for repository operations
- Git hooks for automated validation
- CI/CD systems for testing and deployment
- Code quality tools (ESLint, Prettier, SonarQube)
- Security scanning tools (npm audit, CodeQL)

**Customization Options:**
- Configure complexity thresholds for OODA activation
- Set project-specific validation rules
- Define custom commit message templates
- Configure automatic PR creation and assignment
- Set up custom quality gates and metrics

**Learning and Adaptation:**
- Track success metrics and failure patterns
- Adapt complexity thresholds based on project needs
- Learn from user preferences and team workflows
- Improve risk assessment accuracy over time
- Optimize execution paths for efficiency

This command exemplifies the OODA methodology by providing systematic decision-making that scales from simple to complex scenarios while maintaining military precision in execution.