# Claude Code Testing Framework

A comprehensive testing framework for validating Claude Code best practices and OODA agent workflow integration.

## Overview

This testing framework provides systematic validation of:
- All Claude Code best practices with practical examples
- OODA agent workflow integration patterns
- Step-by-step validation procedures
- Performance benchmarks and metrics
- Quality assurance for agentic coding workflows

## Testing Categories

### 1. Setup and Configuration Tests

#### 1.1 CLAUDE.md File Tests

**Test: CLAUDE.md File Discovery**
```bash
# Test that Claude can find CLAUDE.md files in various locations
test_claude_md_discovery() {
    # Test root directory CLAUDE.md
    echo "# Test CLAUDE.md" > CLAUDE.md
    claude_test_context_includes "Test CLAUDE.md"
    
    # Test parent directory CLAUDE.md
    mkdir -p subdir
    cd subdir
    claude_test_context_includes "Test CLAUDE.md"
    
    # Test home directory CLAUDE.md
    echo "# Global CLAUDE.md" > ~/.claude/CLAUDE.md
    claude_test_context_includes "Global CLAUDE.md"
    
    # Clean up
    rm CLAUDE.md ~/.claude/CLAUDE.md
    rm -rf subdir
}
```

**Test: CLAUDE.md Content Effectiveness**
```bash
# Test that CLAUDE.md instructions are followed
test_claude_md_effectiveness() {
    cat > CLAUDE.md << 'EOF'
# Code Style
- IMPORTANT: Always use TypeScript strict mode
- YOU MUST use semicolons at the end of statements
- Prefer const over let when possible

# Testing
- Run `npm test` before committing
- Use Jest for unit tests
EOF
    
    # Test that Claude follows the style guidelines
    claude_request "Create a simple TypeScript function"
    claude_output_contains "strict"
    claude_output_contains ";"
    claude_output_contains "const"
    
    rm CLAUDE.md
}
```

#### 1.2 Tool Permission Tests

**Test: Tool Allowlist Configuration**
```bash
# Test tool permission management
test_tool_permissions() {
    # Test default conservative permissions
    claude_test_permission_requested "Edit"
    claude_test_permission_requested "Bash(git commit)"
    
    # Test /permissions command
    claude_run "/permissions add Edit"
    claude_test_permission_allowed "Edit"
    
    # Test settings.json modification
    echo '{"allowedTools": ["Edit", "Bash(git:*)"]}' > .claude/settings.json
    claude_test_permission_allowed "Edit"
    claude_test_permission_allowed "Bash(git commit)"
    
    # Clean up
    rm .claude/settings.json
}
```

### 2. Tool Integration Tests

#### 2.1 Bash Environment Tests

**Test: Custom Bash Tool Recognition**
```bash
# Test that Claude can use custom bash tools
test_custom_bash_tools() {
    # Create a custom tool
    cat > custom_tool.sh << 'EOF'
#!/bin/bash
echo "Custom tool executed with args: $*"
EOF
    chmod +x custom_tool.sh
    export PATH="$PWD:$PATH"
    
    # Test Claude can discover and use the tool
    claude_request "Use custom_tool.sh with argument 'test'"
    claude_output_contains "Custom tool executed with args: test"
    
    # Clean up
    rm custom_tool.sh
}
```

#### 2.2 MCP Integration Tests

**Test: MCP Server Configuration**
```bash
# Test MCP server integration
test_mcp_integration() {
    # Create test .mcp.json
    cat > .mcp.json << 'EOF'
{
  "servers": {
    "test-server": {
      "command": "echo",
      "args": ["test-mcp-response"]
    }
  }
}
EOF
    
    # Test MCP server is available
    claude_run "--mcp-debug" "List available MCP tools"
    claude_output_contains "test-server"
    
    rm .mcp.json
}
```

#### 2.3 Custom Slash Commands Tests

**Test: Slash Command Creation and Execution**
```bash
# Test custom slash command functionality
test_slash_commands() {
    mkdir -p .claude/commands
    
    cat > .claude/commands/test-command.md << 'EOF'
Test command with arguments: $ARGUMENTS

Steps:
1. Echo the arguments
2. Create a test file with the content
EOF
    
    # Test command is available
    claude_run "/test-command hello world"
    claude_output_contains "hello world"
    
    # Clean up
    rm -rf .claude/commands
}
```

### 3. Workflow Pattern Tests

#### 3.1 Explore, Plan, Code, Commit Workflow Test

**Test: Complete EPCC Workflow**
```bash
test_epcc_workflow() {
    # Initialize test repository
    git init test-repo
    cd test-repo
    
    # Create initial codebase
    cat > app.js << 'EOF'
const express = require('express');
const app = express();
app.listen(3000);
EOF
    git add . && git commit -m "Initial commit"
    
    # Test Explore phase
    claude_request "Explore this codebase and explain its structure"
    claude_output_contains "express"
    claude_output_contains "app.js"
    
    # Test Plan phase
    claude_request "Plan implementation of a /health endpoint"
    claude_output_contains "GET /health"
    claude_output_contains "200 status"
    
    # Test Code phase
    claude_request "Implement the planned /health endpoint"
    file_contains "app.js" "app.get('/health'"
    
    # Test Commit phase
    claude_request "Create a commit for the health endpoint"
    git_has_commit_containing "health"
    
    # Clean up
    cd .. && rm -rf test-repo
}
```

#### 3.2 Test-Driven Development Workflow Test

**Test: TDD with Claude**
```bash
test_tdd_workflow() {
    # Create test project
    npm init -y
    npm install --save-dev jest
    
    # Test: Write tests first
    claude_request "Create tests for a Calculator class with add, subtract methods"
    file_exists "calculator.test.js"
    test_file_contains_test_cases "calculator.test.js" "add" "subtract"
    
    # Test: Commit failing tests
    claude_request "Commit the failing tests"
    git_has_commit_containing "tests"
    
    # Test: Implement to pass tests
    claude_request "Implement Calculator class to make tests pass"
    file_exists "calculator.js"
    npm run test && test_passes
    
    # Test: Final commit
    claude_request "Commit the working implementation"
    git_has_commit_containing "implementation"
    
    # Clean up
    rm -rf node_modules package*.json *.js
}
```

#### 3.3 UI Development with Screenshots Test

**Test: Visual Feedback Workflow**
```bash
test_ui_screenshot_workflow() {
    # Create simple HTML page
    claude_request "Create a simple HTML page with a centered blue button"
    file_exists "index.html"
    file_contains "index.html" "<button"
    
    # Simulate screenshot feedback (in real test, would use actual screenshot)
    screenshot_path="/tmp/test_ui_screenshot.png"
    create_test_screenshot $screenshot_path
    
    # Test: Claude can analyze screenshot
    claude_request_with_image "Analyze this screenshot and suggest improvements" $screenshot_path
    claude_output_contains "button"
    claude_output_contains "improve" || claude_output_contains "change"
    
    # Test: Implement suggestions
    claude_request "Implement the suggested improvements"
    file_modified_after "index.html" $initial_time
    
    # Clean up
    rm index.html $screenshot_path
}
```

### 4. Workflow Optimization Tests

#### 4.1 Instruction Specificity Tests

**Test: Specific vs Vague Instructions**
```bash
test_instruction_specificity() {
    # Test vague instruction
    vague_response=$(claude_request "Make this code better" --code "function add(a,b){return a+b}")
    
    # Test specific instruction
    specific_response=$(claude_request "Add TypeScript types, error handling for non-numbers, and JSDoc comments" --code "function add(a,b){return a+b}")
    
    # Specific instruction should produce better results
    assert_response_contains_types "$specific_response"
    assert_response_contains_error_handling "$specific_response"
    assert_response_contains_jsdoc "$specific_response"
    
    assert_response_quality_higher "$specific_response" "$vague_response"
}
```

#### 4.2 File Context Tests

**Test: File Context Effectiveness**
```bash
test_file_context() {
    # Create test files
    create_test_auth_files
    
    # Test without file context
    no_context_response=$(claude_request "Implement logout functionality")
    
    # Test with file context
    context_response=$(claude_request "Look at src/auth.js and src/user.js, then implement logout functionality")
    
    # Context should produce more specific results
    assert_response_references_existing_code "$context_response"
    assert_response_follows_patterns "$context_response"
    
    # Clean up
    rm -rf src/
}
```

### 5. Headless Mode and Automation Tests

#### 5.1 Issue Triage Automation Test

**Test: Automated Issue Processing**
```bash
test_automated_issue_triage() {
    # Setup mock GitHub repository
    setup_mock_github_repo
    
    # Create test issues
    create_test_issues
    
    # Test automated triage
    claude_headless "Analyze GitHub issues and add appropriate labels"
    
    # Verify issues were processed
    assert_issue_has_label "1" "bug"
    assert_issue_has_label "2" "feature"
    assert_issue_has_label "3" "documentation"
    
    # Clean up
    cleanup_mock_github_repo
}
```

#### 5.2 Code Linting Automation Test

**Test: Automated Code Review**
```bash
test_automated_linting() {
    # Create code with various issues
    create_test_code_with_issues
    
    # Run automated linting
    claude_headless "Review all Python files for code style, security, and best practices"
    
    # Verify report was generated
    file_exists "code_review_report.md"
    file_contains "code_review_report.md" "security"
    file_contains "code_review_report.md" "style"
    file_contains "code_review_report.md" "recommendations"
    
    # Clean up
    rm -rf src/ code_review_report.md
}
```

### 6. Multi-Claude Workflow Tests

#### 6.1 Writer-Reviewer Pattern Test

**Test: Dual Claude Code Review**
```bash
test_multi_claude_workflow() {
    # Writer Claude implementation
    writer_output=$(claude_session_1 "Implement a user authentication system")
    
    # Save implementation
    echo "$writer_output" > auth_implementation.py
    
    # Reviewer Claude analysis
    reviewer_output=$(claude_session_2 "Review this authentication code for security issues and improvements" --file auth_implementation.py)
    
    # Verify review process
    assert_contains "$reviewer_output" "security"
    assert_contains "$reviewer_output" "improvement"
    assert_contains "$reviewer_output" "recommendation"
    
    # Clean up
    rm auth_implementation.py
}
```

### 7. OODA Integration Tests

#### 7.1 Observe Phase Integration

**Test: OODA Observe with Claude Code**
```bash
test_ooda_observe() {
    # Create codebase to observe
    setup_complex_codebase
    
    # Use Claude for systematic observation
    claude_request "Act as OODA Observe agent: systematically analyze this codebase structure, dependencies, and patterns"
    
    # Verify comprehensive observation
    claude_output_contains "dependencies"
    claude_output_contains "architecture"
    claude_output_contains "patterns"
    claude_output_contains "issues"
    
    # Clean up
    cleanup_complex_codebase
}
```

#### 7.2 Orient Phase Integration

**Test: OODA Orient with Claude Code**
```bash
test_ooda_orient() {
    # Provide observation data
    observation_data=$(cat observation_report.md)
    
    # Use Claude for orientation analysis
    claude_request "Act as OODA Orient agent: analyze this observation data and identify strategic options for improvement" --data "$observation_data"
    
    # Verify strategic thinking
    claude_output_contains "options"
    claude_output_contains "strategy"
    claude_output_contains "priorities"
    claude_output_contains "trade-offs"
}
```

#### 7.3 Decide Phase Integration

**Test: OODA Decide with Claude Code**
```bash
test_ooda_decide() {
    # Provide oriented analysis
    oriented_analysis=$(cat orientation_report.md)
    
    # Use Claude for decision making
    claude_request "Act as OODA Decide agent: choose the optimal implementation approach from these options" --data "$oriented_analysis"
    
    # Verify decision quality
    claude_output_contains "chosen approach"
    claude_output_contains "rationale"
    claude_output_contains "implementation plan"
    claude_output_contains "success criteria"
}
```

#### 7.4 Act Phase Integration

**Test: OODA Act with Claude Code**
```bash
test_ooda_act() {
    # Provide decision and implementation plan
    implementation_plan=$(cat implementation_plan.md)
    
    # Use Claude for execution
    claude_request "Act as OODA Act agent: execute this implementation plan with precision" --data "$implementation_plan"
    
    # Verify execution
    assert_implementation_completed
    assert_tests_pass
    assert_code_quality_maintained
    assert_documentation_updated
}
```

### 8. Performance and Benchmark Tests

#### 8.1 Context Loading Performance

**Test: Context Loading Efficiency**
```bash
test_context_loading_performance() {
    # Create large codebase
    create_large_test_codebase 1000 # 1000 files
    
    # Measure context loading time
    start_time=$(date +%s%N)
    claude_request "Analyze this codebase"
    end_time=$(date +%s%N)
    
    loading_time=$((($end_time - $start_time) / 1000000)) # Convert to milliseconds
    
    # Assert performance benchmarks
    assert_less_than $loading_time 30000 # Less than 30 seconds
    
    # Clean up
    cleanup_large_test_codebase
}
```

#### 8.2 Response Quality Metrics

**Test: Response Quality Measurement**
```bash
test_response_quality() {
    # Test various request types
    test_cases=(
        "simple_function_creation"
        "complex_refactoring"
        "bug_fix_with_tests"
        "documentation_generation"
    )
    
    for test_case in "${test_cases[@]}"; do
        response=$(run_quality_test $test_case)
        
        # Measure quality metrics
        code_correctness=$(measure_code_correctness "$response")
        completeness=$(measure_completeness "$response")
        maintainability=$(measure_maintainability "$response")
        
        # Assert quality thresholds
        assert_greater_than $code_correctness 0.8
        assert_greater_than $completeness 0.9
        assert_greater_than $maintainability 0.7
    done
}
```

## Test Execution Framework

### Test Runner

```bash
#!/bin/bash
# test_runner.sh - Main test execution script

set -e

# Configuration
CLAUDE_TEST_DIR="./claude_tests"
REPORT_FILE="test_report.md"
LOG_FILE="test_execution.log"

# Test categories
CATEGORIES=(
    "setup_configuration"
    "tool_integration" 
    "workflow_patterns"
    "optimization"
    "automation"
    "multi_claude"
    "ooda_integration"
    "performance"
)

run_test_suite() {
    local category=$1
    echo "Running $category tests..."
    
    for test_file in $CLAUDE_TEST_DIR/${category}_*.sh; do
        if [ -f "$test_file" ]; then
            echo "  Executing: $test_file"
            bash "$test_file" >> $LOG_FILE 2>&1 || {
                echo "  FAILED: $test_file"
                return 1
            }
            echo "  PASSED: $test_file"
        fi
    done
}

main() {
    echo "Claude Code Testing Framework"
    echo "============================="
    echo "Start time: $(date)"
    
    # Create test report
    cat > $REPORT_FILE << EOF
# Claude Code Test Results
Generated: $(date)

## Test Summary
EOF
    
    passed=0
    failed=0
    
    for category in "${CATEGORIES[@]}"; do
        echo "Testing category: $category"
        if run_test_suite $category; then
            echo "✅ $category: PASSED" >> $REPORT_FILE
            ((passed++))
        else
            echo "❌ $category: FAILED" >> $REPORT_FILE
            ((failed++))
        fi
    done
    
    # Generate summary
    cat >> $REPORT_FILE << EOF

## Summary
- Passed: $passed
- Failed: $failed  
- Total: $((passed + failed))
- Success Rate: $(( (passed * 100) / (passed + failed) ))%

## Detailed Logs
See $LOG_FILE for detailed execution logs.
EOF
    
    echo "Testing completed. Report: $REPORT_FILE"
    
    if [ $failed -gt 0 ]; then
        exit 1
    fi
}

main "$@"
```

### Test Utilities

```bash
# test_utils.sh - Common testing utilities

# Claude interaction utilities
claude_request() {
    local prompt="$1"
    local options="$2"
    
    echo "$prompt" | claude $options
}

claude_headless() {
    local prompt="$1"
    claude --headless "$prompt"
}

claude_output_contains() {
    local text="$1"
    local output="$2"
    
    if echo "$output" | grep -q "$text"; then
        return 0
    else
        echo "Expected output to contain: $text"
        return 1
    fi
}

# File system utilities
file_exists() {
    local file="$1"
    [ -f "$file" ]
}

file_contains() {
    local file="$1"
    local text="$2"
    
    grep -q "$text" "$file"
}

file_modified_after() {
    local file="$1" 
    local timestamp="$2"
    
    [ "$file" -nt "$timestamp" ]
}

# Git utilities
git_has_commit_containing() {
    local text="$1"
    git log --oneline | grep -q "$text"
}

# Quality measurement utilities
measure_code_correctness() {
    local code="$1"
    # Implementation would analyze syntax, logic, etc.
    # Return score 0.0-1.0
    echo "0.85"
}

measure_completeness() {
    local response="$1"
    # Implementation would check if all requirements addressed
    # Return score 0.0-1.0  
    echo "0.92"
}

measure_maintainability() {
    local code="$1"
    # Implementation would analyze code quality metrics
    # Return score 0.0-1.0
    echo "0.78"
}

# Assertion utilities
assert_greater_than() {
    local actual="$1"
    local expected="$2"
    
    if (( $(echo "$actual > $expected" | bc -l) )); then
        return 0
    else
        echo "Assertion failed: $actual > $expected"
        return 1
    fi
}

assert_contains() {
    local text="$1"
    local content="$2"
    
    if echo "$content" | grep -q "$text"; then
        return 0
    else
        echo "Assertion failed: content should contain '$text'"
        return 1
    fi
}
```

## Continuous Integration Integration

### GitHub Actions Workflow

```yaml
# .github/workflows/claude-code-tests.yml
name: Claude Code Testing Framework

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Install Claude Code
      run: |
        # Installation commands for Claude Code
        curl -sSL https://claude.ai/install | sh
    
    - name: Setup Test Environment
      run: |
        chmod +x ./tests/test_runner.sh
        chmod +x ./tests/test_utils.sh
        
    - name: Run Claude Code Tests
      run: |
        ./tests/test_runner.sh
        
    - name: Upload Test Reports
      uses: actions/upload-artifact@v3
      if: always()
      with:
        name: test-reports
        path: |
          test_report.md
          test_execution.log
          
    - name: Comment Test Results
      if: github.event_name == 'pull_request'
      uses: actions/github-script@v6
      with:
        script: |
          const fs = require('fs');
          const report = fs.readFileSync('test_report.md', 'utf8');
          github.rest.issues.createComment({
            issue_number: context.issue.number,
            owner: context.repo.owner,
            repo: context.repo.repo,
            body: `## Claude Code Test Results\n\n${report}`
          });
```

## Usage Examples

### Running Individual Tests

```bash
# Run specific test category
./tests/test_runner.sh setup_configuration

# Run specific test file
bash ./tests/setup_configuration_claude_md.sh

# Run with verbose output
VERBOSE=1 ./tests/test_runner.sh
```

### Custom Test Creation

```bash
# Create new test file
cat > tests/custom_workflow_test.sh << 'EOF'
#!/bin/bash
source ./test_utils.sh

test_custom_workflow() {
    echo "Testing custom workflow..."
    
    # Your test implementation here
    claude_request "Your test prompt"
    
    # Assertions
    assert_contains "expected_output" "$result"
    
    echo "✅ Custom workflow test passed"
}

# Run the test
test_custom_workflow
EOF

chmod +x tests/custom_workflow_test.sh
```

## Quality Assurance Standards

### Test Quality Checklist

- [ ] **Isolation**: Each test runs independently
- [ ] **Repeatability**: Tests produce consistent results
- [ ] **Coverage**: All documented features are tested
- [ ] **Realistic**: Tests use realistic scenarios
- [ ] **Measurable**: Clear pass/fail criteria
- [ ] **Maintainable**: Tests are easy to understand and modify
- [ ] **Fast**: Tests complete within reasonable time
- [ ] **Reliable**: Minimal flaky test failures

### Success Criteria

**Functional Tests**
- 95% test pass rate for core functionality
- All documented workflows validated
- Integration points working correctly

**Performance Tests**
- Context loading < 30 seconds for large codebases
- Response time < 10 seconds for typical requests
- Memory usage stays within acceptable bounds

**Quality Tests**  
- Code correctness score > 0.8
- Response completeness score > 0.9
- Maintainability score > 0.7

This comprehensive testing framework ensures that Claude Code best practices are not just documented but actively validated, providing confidence in the reliability and effectiveness of agentic coding workflows integrated with OODA methodology.