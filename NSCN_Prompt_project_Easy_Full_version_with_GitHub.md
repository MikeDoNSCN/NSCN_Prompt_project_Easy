# 🚀 NNNNN Automation Template - Full Version with Git/GitHub

Complete template for module-based development with NNNNN automation, Git/GitHub integration, maximizing reusability and MCP integration.

---

# Create [PROJECT_NAME] with GitHub Integration & NNNNN Automation

## 📋 Project Context:
[Provide ANY of these:]
- Previous conversations
- PRD/Requirements
- Technical specifications  
- Project ideas/notes
- Reference implementations

## 🎯 Project Configuration:
```yaml
project_name: "[PROJECT_NAME]"
project_slug: "[project-name-kebab]"  
package_name: "[project_name_snake]"
github_repo: "[username]/[project-name]"
project_root: "%PROJECTS%/[project-name]"
estimated_modules: [number]
license: "MIT"  # or Apache-2.0, GPL-3.0, etc.
python_version: "3.8+"
mcp_enabled: true  # Use MCP Desktop Commander
module_token_limit: 300  # HARD LIMIT per module
```

## 🎨 Design Principles:
1. **Maximize Reusability** - Extract common patterns into shared modules
2. **MCP First** - Use MCP tools instead of manual file operations
3. **Micro-Modules** - Each module MUST be <300 tokens
4. **Error Prevention** - Centralized error handling to save tokens
5. **Git Integration** - Track progress with commits and PRs

## 📁 Create Complete GitHub Repository Structure:

### 1. GitHub Configuration Files

#### `.github/workflows/ci.yml`
```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: [3.8, 3.9, 3.10, 3.11]
    
    steps:
    - uses: actions/checkout@v3
    - name: Set up Python ${{ matrix.python-version }}
      uses: actions/setup-python@v4
      with:
        python-version: ${{ matrix.python-version }}
    
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
        pip install -r requirements-dev.txt
    
    - name: Run tests
      run: |
        pytest tests/ --cov=src/[package_name] --cov-report=xml
    
    - name: Upload coverage
      uses: codecov/codecov-action@v3
```

#### `.github/workflows/nnnnn-tracker.yml`
```yaml
name: NNNNN Progress Tracker

on:
  push:
    paths:
      - '_dev/module_status.json'
      - 'src/**/*.py'

jobs:
  track-progress:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Calculate Progress
      run: |
        python _dev/scripts/calculate_progress.py
    
    - name: Update README Badge
      run: |
        python _dev/scripts/update_badge.py
    
    - name: Commit updates
      uses: stefanzweifel/git-auto-commit-action@v4
      with:
        commit_message: 'Update NNNNN progress'
```

#### `.github/ISSUE_TEMPLATE/module_implementation.md`
```markdown
---
name: Module Implementation
about: Track NNNNN module implementation
title: '[NNNNN] Module XXXX: [Name]'
labels: nnnnn, module, implementation
assignees: ''
---

## Module Details
- **ID**: XXXX
- **Name**: [Module name]
- **Token Limit**: XXX/300
- **File**: `src/[package_name]/[path]`
- **MCP Tools**: [list MCP tools used]
- **Reusability**: [High/Medium/Low]

## Dependencies
- [ ] Module XXXX
- [ ] Module YYYY

## Implementation Checklist
- [ ] Core functionality (<300 tokens)
- [ ] Error handling via decorator
- [ ] MCP tools used (not stdio)
- [ ] Unit tests
- [ ] Documentation
- [ ] Reusability tracked

## Notes
[Any special considerations]
```

### 2. Project Root Files

#### `README.md`
```markdown
# [PROJECT_NAME]

[![CI/CD](https://github.com/[username]/[project-name]/actions/workflows/ci.yml/badge.svg)](https://github.com/[username]/[project-name]/actions/workflows/ci.yml)
[![codecov](https://codecov.io/gh/[username]/[project-name]/branch/main/graph/badge.svg)](https://codecov.io/gh/[username]/[project-name])
[![NNNNN Progress](https://img.shields.io/badge/NNNNN-0%2F[total]-blue)](/_dev/module_status.json)
[![Reusability](https://img.shields.io/badge/Reusability-0%25-orange)](/_dev/reusability_tracker.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[Project description]

## 🚀 Features

[List main features based on PRD]

## 📦 Installation

```bash
pip install [project-name]
```

## 🔧 Development Setup

```bash
# Clone repository
git clone https://github.com/[username]/[project-name].git
cd [project-name]

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install in development mode
pip install -e ".[dev]"

# Setup pre-commit hooks
pre-commit install
```

## 🤖 NNNNN Development

This project uses NNNNN automation for development:

```bash
# In Claude Desktop (with MCP)
NNNNN          # Implement next module
NNNNN x 10     # Implement 10 modules
status         # Check progress
reuse-stats    # Check reusability metrics
```

See [PROJECT_INSTRUCTIONS.md](PROJECT_INSTRUCTIONS.md) for details.

## 📊 Module Progress

| Phase | Modules | Status | Reusability |
|-------|---------|--------|-------------|
| Core | 0001-0030 | ⏳ 0/30 | 0% |
| Features | 0031-0080 | ⏳ 0/50 | 0% |
| Integration | 0081-0120 | ⏳ 0/40 | 0% |
| **Total** | **[total]** | **⏳ 0/[total]** | **0%** |

## 🧪 Testing

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src/[package_name]

# Run specific test
pytest tests/test_module.py::test_function
```

## 📖 Documentation

Full documentation at: [https://[username].github.io/[project-name]/](https://[username].github.io/[project-name]/)

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file.
```

#### `CONTRIBUTING.md`
```markdown
# Contributing to [PROJECT_NAME]

## Development Process

1. Create issue for module implementation
2. Create feature branch: `module-XXXX`
3. Implement using NNNNN
4. Create PR linking to issue
5. Pass CI/CD checks
6. Merge to develop

## NNNNN Guidelines

- Each module MUST be <300 tokens
- Use MCP for all file operations
- Maximize reusability (target 40%)
- Update tracking files

## Code Standards

- Type hints required
- Docstrings for all public functions
- Black formatting
- Flake8 compliance
- Mypy type checking
```

### 3. Pre-commit Configuration

#### `.pre-commit-config.yaml`
```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-added-large-files
      
  - repo: https://github.com/psf/black
    rev: 22.10.0
    hooks:
      - id: black
        
  - repo: https://github.com/PyCQA/flake8
    rev: 5.0.4
    hooks:
      - id: flake8
        args: ['--max-line-length=88']
        
  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v0.990
    hooks:
      - id: mypy
        additional_dependencies: [types-all]
```

### 4. GitHub Actions for NNNNN

#### `.github/workflows/nnnnn-automation.yml`
```yaml
name: NNNNN Automation Helper

on:
  schedule:
    - cron: '0 0 * * *'  # Daily progress check
  workflow_dispatch:
    inputs:
      modules_to_implement:
        description: 'Number of modules to implement'
        required: false
        default: '10'

jobs:
  check-progress:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.10'
    
    - name: Check Module Progress
      run: |
        python _dev/scripts/check_progress.py
    
    - name: Check Reusability Metrics
      run: |
        python _dev/scripts/check_reusability.py
    
    - name: Create Issues for Next Modules
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      run: |
        python _dev/scripts/create_module_issues.py \
          --count ${{ github.event.inputs.modules_to_implement || 10 }}
    
    - name: Update Project Board
      run: |
        python _dev/scripts/update_project_board.py
```

### 5. Development Scripts

#### `_dev/scripts/check_progress.py`
```python
#!/usr/bin/env python3
"""Check NNNNN implementation progress"""
import json
from pathlib import Path

def check_progress():
    status_file = Path("_dev/module_status.json")
    with open(status_file) as f:
        status = json.load(f)
    
    completed = sum(1 for m in status["modules"].values() 
                   if m["status"] == "completed")
    total = status["total_modules"]
    percentage = (completed / total) * 100
    
    # Check reusability
    reuse_percentage = status["reusability_metrics"]["actual_percentage"]
    tokens_saved = status["reusability_metrics"]["tokens_saved"]
    
    print(f"NNNNN Progress: {completed}/{total} ({percentage:.1f}%)")
    print(f"Reusability: {reuse_percentage:.1f}% (Target: 40%)")
    print(f"Tokens Saved: {tokens_saved}")
    
    # Update README badges
    update_badges(percentage, reuse_percentage)
    
    # Generate progress report
    generate_report(status)

if __name__ == "__main__":
    check_progress()
```

#### `_dev/scripts/create_module_issues.py`
```python
#!/usr/bin/env python3
"""Create GitHub issues for next modules"""
import json
import os
from github import Github

def create_module_issues(count=10):
    g = Github(os.environ['GITHUB_TOKEN'])
    repo = g.get_repo(os.environ['GITHUB_REPOSITORY'])
    
    with open('_dev/module_status.json') as f:
        status = json.load(f)
    
    # Find next modules to implement
    pending_modules = [
        (id, info) for id, info in status['modules'].items()
        if info['status'] == 'pending' and
        all(status['modules'][dep]['status'] == 'completed' 
            for dep in info['dependencies'])
    ][:count]
    
    for module_id, module_info in pending_modules:
        # Create issue
        title = f"[NNNNN] Module {module_id}: {module_info['name']}"
        body = f"""
## Module Details
- **ID**: {module_id}
- **Name**: {module_info['name']}
- **Token Limit**: {module_info['tokens']}/300
- **File**: `{module_info['file']}`
- **MCP Tools**: {', '.join(module_info['mcp_tools'])}
- **Dependencies**: {', '.join(module_info['dependencies'])}

## Implementation
Use NNNNN command to implement this module.
        """
        
        issue = repo.create_issue(
            title=title,
            body=body,
            labels=['nnnnn', 'module', 'implementation']
        )
        print(f"Created issue #{issue.number} for module {module_id}")

if __name__ == "__main__":
    import argparse
    parser = argparse.ArgumentParser()
    parser.add_argument('--count', type=int, default=10)
    args = parser.parse_args()
    create_module_issues(args.count)
```

### 6. Git Integration in NNNNN

#### `PROJECT_INSTRUCTIONS.md` (Git Section)
```markdown
## Git Integration

### Branch Strategy
- `main` - Stable releases
- `develop` - Integration branch
- `module-XXXX` - Feature branches for modules

### NNNNN Git Workflow
1. Create branch: `git checkout -b module-XXXX`
2. Implement module via NNNNN
3. Commit: `git commit -m "feat: implement module XXXX - [name]"`
4. Push: `git push origin module-XXXX`
5. Create PR linking to issue

### Commit Message Format
```
feat: implement module XXXX - [module name]

- Token usage: XXX/300
- MCP tools: [list]
- Reused components: [list]
- Tokens saved: XXX

Closes #[issue-number]
```

### PR Template
```markdown
## Module Implementation

**Module**: XXXX - [Name]
**Token Usage**: XXX/300
**Reusability**: [%]

### Checklist
- [ ] Under 300 tokens
- [ ] Uses MCP tools
- [ ] Tests pass
- [ ] Reusability tracked
```
```

[Rest of the template continues with all standard sections from the simple version: pyproject.toml, source structure, development automation files, testing, shared infrastructure, etc.]

---

## 🎯 Complete Git-Integrated Workflow

1. **Initial Setup**
   ```bash
   # Create GitHub repo
   gh repo create [project-name] --public
   
   # Clone and setup
   git clone https://github.com/[username]/[project-name]
   cd [project-name]
   
   # Run initial NNNNN setup
   # Claude creates all files with MCP
   
   # Initial commit
   git add .
   git commit -m "initial: project structure with NNNNN automation"
   git push origin main
   ```

2. **NNNNN Development with Git**
   ```
   # Create issue
   You: create-issue 0001
   
   # Create branch
   git checkout -b module-0001
   
   # Implement
   You: NNNNN
   Claude: ✅ Implemented Module 0001
   
   # Commit and push
   git add .
   git commit -m "feat: implement module 0001 - File Drop Zone"
   git push origin module-0001
   
   # Create PR
   gh pr create --fill
   ```

3. **CI/CD Integration**
   - Tests run automatically on PR
   - Coverage reported
   - Progress badges updated
   - Reusability metrics tracked

---

END OF FULL GIT VERSION