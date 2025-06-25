# 🚀 NNNNN Automation Template - Simple Version

Complete template for module-based development with NNNNN automation, maximizing reusability and MCP integration.

---

# Create [PROJECT_NAME] with NNNNN Automation

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
package_name: "[project_name_snake]"
project_root: "%PROJECTS%/[PROJECT_NAME]"
estimated_modules: [number]
python_version: "3.8+"
mcp_enabled: true  # Use MCP Desktop Commander
module_token_limit: 300  # HARD LIMIT per module
```

## 🎨 Design Principles:
1. **Maximize Reusability** - Extract common patterns into shared modules
2. **MCP First** - Use MCP tools instead of manual file operations
3. **Micro-Modules** - Each module MUST be <300 tokens
4. **Error Prevention** - Centralized error handling to save tokens

## 📁 Create Complete Project Structure:

### 1. Project Root Files

#### `README.md`
```markdown
# [PROJECT_NAME]

[![NNNNN Progress](https://img.shields.io/badge/NNNNN-0%2F[total]-blue)](/_dev/module_status.json)
[![Reusability](https://img.shields.io/badge/Reusability-0%25-orange)](/_dev/reusability_tracker.md)

[Project description]

## 🚀 Features

[List main features based on PRD]

## 📦 Installation

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install in development mode
pip install -e .
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
```

#### `pyproject.toml`
```toml
[build-system]
requires = ["setuptools>=61.0", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "[project-name]"
version = "0.1.0"
description = "[Project description]"
readme = "README.md"
authors = [
    {name = "[Your Name]", email = "[your.email@example.com]"}
]
requires-python = ">=3.8"
dependencies = [
    # Add from requirements.txt
]

[project.optional-dependencies]
dev = [
    "pytest>=7.0.0",
    "pytest-cov>=4.0.0",
    "black>=22.0.0",
    "flake8>=5.0.0",
    "mypy>=0.990",
]

[tool.black]
line-length = 88
target-version = ['py38']

[tool.mypy]
python_version = "3.8"
warn_return_any = true
warn_unused_configs = true

[tool.pytest.ini_options]
testpaths = ["tests"]
python_files = ["test_*.py"]
```

### 2. Source Code Structure

#### `src/[package_name]/__init__.py`
```python
"""[PROJECT_NAME] - [Brief description]"""

__version__ = "0.1.0"
__author__ = "[Your Name]"
__email__ = "[your.email@example.com]"

# Imports will be added via NNNNN
```

### 3. Development Automation Files

#### `_dev/IMPLEMENTATION_PLAN.md`
```markdown
# Implementation Plan - [PROJECT_NAME]

## Overview
Total Modules: [number]
Token Limit: 300 per module (STRICT)
Architecture: [Brief description]
Reusability Target: 40%+ code reuse

## Module Breakdown

### Phase 1: Core Infrastructure (Modules 0001-0030)

#### Module 0001: [Name]
- **Tokens**: XXX/300
- **File**: src/[package_name]/core/[file].py
- **Purpose**: [Description]
- **Dependencies**: None
- **MCP Tools**: [e.g., read_file, write_file]
- **Reusability**: High/Medium/Low
- **Exports**: [Functions/Classes]

#### Module 0002: [Name]
[Continue for all modules...]

## Reusability Strategy
1. **Shared Components** (src/[package_name]/shared/)
   - error_handler.py - Saves ~100 tokens per module
   - mcp_wrapper.py - Standardized MCP operations
   - validators.py - Common validation functions
   
2. **Token Savings Tracker**
   - Target: Save 40% tokens through reuse
   - Track actual savings per module
```

#### `_dev/module_status.json`
```json
{
  "project": "[project-name]",
  "total_modules": [number],
  "completed": 0,
  "in_progress": 0,
  "reusability_metrics": {
    "target_percentage": 40,
    "actual_percentage": 0,
    "tokens_saved": 0,
    "shared_components_used": {}
  },
  "phases": {
    "core": {"start": 1, "end": 30, "completed": 0},
    "features": {"start": 31, "end": 80, "completed": 0},
    "integration": {"start": 81, "end": 120, "completed": 0}
  },
  "modules": {
    "0001": {
      "name": "[Module name]",
      "status": "pending",
      "tokens": XXX,
      "file": "src/[package_name]/core/[file].py",
      "dependencies": [],
      "mcp_tools": ["read_file", "write_file"],
      "reused_components": []
    }
  }
}
```

#### `_dev/reusability_tracker.md`
```markdown
# Reusability Tracker

## Shared Components Library

### Error Handling
- **Component**: @safe_module decorator
- **Location**: shared/error_handler.py
- **Token Savings**: ~100 per use
- **Used In**: All modules

### MCP Operations
- **Component**: MCPWrapper
- **Location**: shared/mcp_wrapper.py
- **Token Savings**: ~50 per file operation
- **Used In**: Modules doing file I/O

### Validators
- **Component**: Common validators
- **Location**: shared/validators.py
- **Token Savings**: ~30-50 per validation
- **Used In**: Input processing modules

## Reusability Metrics
- Total Modules: [number]
- Modules Using Shared Code: 0
- Average Token Savings: 0
- Total Tokens Saved: 0

## Extraction Candidates
[Track patterns that appear 3+ times for extraction]
```

#### `PROJECT_INSTRUCTIONS.md`
```markdown
# NNNNN Automation Instructions

## Quick Commands
- `NNNNN` - Implement next module with satisfied dependencies
- `NNNNN x 10` - Implement next 10 modules  
- `status` - Show progress overview
- `module XXXX` - Implement specific module
- `deps XXXX` - Show dependencies for module
- `reuse-stats` - Show reusability metrics

## Automatic Workflow
When user types "NNNNN":
1. Read `_dev/module_status.json` using MCP
2. Find next module with satisfied dependencies
3. Check for reusable components
4. Implement module (<300 tokens STRICT)
5. Track MCP usage and reused components
6. Update all tracking files
7. Show progress summary with token savings

## MCP Usage Requirements
**ALWAYS use MCP Desktop Commander for file operations:**
```python
# ❌ NEVER use standard Python
with open('file.txt', 'r') as f:
    content = f.read()

# ✅ ALWAYS use MCP
content = mcp.read_file('file.txt')
```

**MCP Tools Available:**
- `mcp.read_file(path)` - Read any file
- `mcp.write_file(path, content)` - Write file
- `mcp.create_directory(path)` - Create directory
- `mcp.list_directory(path)` - List contents
- `mcp.web_search(query)` - Search web
- `mcp.google_drive_search(query)` - Search Drive

## Module Implementation Standards
- **Maximum 300 tokens per module** (HARD LIMIT)
- **Use shared components** to save tokens
- **Track reusability** in every module
- **Use MCP** for ALL file operations
- **Include type hints**
- **Add docstrings**
- **Follow PEP 8**

## Reusability Guidelines
1. **Use Shared Components:**
   - `@safe_module` decorator (saves ~100 tokens)
   - `MCPWrapper` for file ops (saves ~50 tokens)
   - Common validators (saves ~30-50 tokens)

2. **Extract New Components:**
   - If pattern appears 3+ times → Extract to shared/
   - Document token savings
   - Update reusability_tracker.md

3. **Track Metrics:**
   - Target: 40% token savings through reuse
   - Update module_status.json with reused components
   - Monitor total tokens saved

## Error Documentation
- Update `_dev/ERROR_GUIDE.md` for HIGH/CRITICAL errors
- Include prevention strategies
- Update affected modules
- Note if error pattern should be extracted to shared/
```

### 4. Testing Structure

#### `tests/conftest.py`
```python
"""Pytest configuration"""
import pytest
import sys
from pathlib import Path

# Add src to path
sys.path.insert(0, str(Path(__file__).parent.parent / "src"))

@pytest.fixture
def sample_data():
    """Provide sample data for tests"""
    return {
        # Add test data
    }
```

### 5. Shared Infrastructure for Maximum Reusability

#### `src/[package_name]/shared/error_handler.py`
```python
"""Centralized error handling - saves ~100 tokens per module"""
from functools import wraps
import logging
from typing import Callable, Any

logger = logging.getLogger(__name__)

def safe_module(module_id: str) -> Callable:
    """Decorator for all modules with error handling"""
    def decorator(func: Callable) -> Callable:
        @wraps(func)
        def wrapper(*args: Any, **kwargs: Any) -> Any:
            try:
                logger.debug(f"Module {module_id}: Executing {func.__name__}")
                result = func(*args, **kwargs)
                logger.debug(f"Module {module_id}: Success")
                return result
            except Exception as e:
                logger.error(f"Module {module_id}: {func.__name__} failed - {e}")
                # Module-specific error handling
                if module_id.startswith("00"):  # Core modules
                    raise  # Re-raise for core modules
                return None  # Graceful degradation for features
        return wrapper
    return decorator
```

#### `src/[package_name]/shared/mcp_wrapper.py`
```python
"""MCP operations wrapper - saves ~50 tokens per file operation"""
from typing import Optional, List, Dict, Any
import json

class MCPWrapper:
    """Centralized MCP operations to reduce code duplication"""
    
    @staticmethod
    def safe_read(file_path: str, default: Any = None) -> Any:
        """Read file with error handling"""
        try:
            content = mcp.read_file(file_path)
            if file_path.endswith('.json'):
                return json.loads(content)
            return content
        except Exception as e:
            logger.error(f"Failed to read {file_path}: {e}")
            return default
    
    @staticmethod
    def safe_write(file_path: str, content: Any) -> bool:
        """Write file with error handling"""
        try:
            if isinstance(content, (dict, list)):
                content = json.dumps(content, indent=2)
            mcp.write_file(file_path, content)
            return True
        except Exception as e:
            logger.error(f"Failed to write {file_path}: {e}")
            return False
    
    @staticmethod
    def ensure_directory(dir_path: str) -> bool:
        """Create directory if not exists"""
        try:
            mcp.create_directory(dir_path)
            return True
        except:
            return False
```

#### `src/[package_name]/shared/validators.py`
```python
"""Common validation functions - saves ~30-50 tokens per use"""
from typing import Any, Optional, List

def validate_range(value: float, min_val: float, max_val: float) -> bool:
    """Validate numeric range"""
    return min_val <= value <= max_val

def validate_required(data: dict, required_fields: List[str]) -> bool:
    """Check required fields exist"""
    return all(field in data for field in required_fields)

def validate_type(value: Any, expected_type: type) -> bool:
    """Type validation with None handling"""
    return value is None or isinstance(value, expected_type)
```

### 6. Error Documentation

#### `_dev/ERROR_GUIDE.md`
```markdown
# Error Guide

## Overview
Documents important errors discovered during development.

## Error Severity Levels:
- **CRITICAL**: Affects multiple modules or core architecture
- **HIGH**: Affects current module significantly
- **MEDIUM**: Workaround available but should be fixed
- **LOW**: Minor issue, note for future improvement

## Documented Errors:
[Errors will be added during development]

### Template:
---
## Error: [Error Name]
- **Date**: [YYYY-MM-DD]
- **Severity**: CRITICAL/HIGH/MEDIUM/LOW
- **Discovered in**: Module XX
- **Affects**: Modules [list]
- **Status**: OPEN/RESOLVED

### Description:
[What went wrong]

### Root Cause:
[Why it happened]

### Solution:
[How to fix it]

### Prevention:
[How to avoid in other modules]

### Code Example:
```python
# ❌ Wrong way
[problematic code]

# ✅ Correct way
[fixed code]
```
```

### 7. Module Mapping

#### `MODULE_MAPPING.md`
```markdown
# Module Mapping for [PROJECT_NAME]

## Quick Reference
- Module 0001 → src/[package_name]/core/[file].py - [Description]
- Module 0002 → src/[package_name]/core/[file].py - [Description]
[Continue for all modules...]

## Dependency Graph
```
0001 (No deps)
  └── 0002
      └── 0003
          ├── 0004
          └── 0005
```

## Implementation Order
1. Start with modules with no dependencies
2. Follow dependency graph
3. Complete each phase before moving to next

## Reusability Map
- Modules using @safe_module: ALL
- Modules using MCPWrapper: [list]
- Modules using validators: [list]
```

## 🤖 NNNNN Implementation Behavior

When implementing modules via NNNNN:

1. **Check Dependencies**
   - Only implement if all dependencies satisfied
   - Mark blocked if dependencies incomplete

2. **Follow Standards**
   - Use type hints
   - Include docstrings
   - Apply error decorator
   - Stay under 300 tokens
   - Use MCP for all I/O

3. **Track Metrics**
   - module_status.json
   - Reusability percentage
   - Tokens saved
   - MCP usage

## 📊 Module Structure

Each module follows this pattern:

```python
# -*- coding: utf-8 -*-
"""
Module XXXX: [Name]
Status: pending
Dependencies: [0001, 0002]
MCP Tools: [read_file, write_file]
Reused: [@safe_module, MCPWrapper]
Tokens: ~XXX/300
"""
from [package_name].shared.error_handler import safe_module
from [package_name].shared.mcp_wrapper import MCPWrapper
from typing import [needed types]

# Using shared decorator saves ~100 tokens
@safe_module("XXXX")
def main_function(file_path: str) -> dict:
    """Function description"""
    # Using MCPWrapper saves ~50 tokens vs direct implementation
    mcp = MCPWrapper()
    
    # Read using MCP (not standard Python)
    data = mcp.safe_read(file_path, default={})
    
    # Process data (main logic under 150 tokens)
    result = process_data(data)
    
    # Write using MCP
    mcp.safe_write(f"{file_path}.output", result)
    
    return result
```

## 🎯 Complete Workflow

### 0. **Prerequisites**
   - MCP Desktop Commander MUST be enabled
   - Python 3.8+ installed
   - Project location at %PROJECTS%

### 1. **Initial Setup**
   - Create project structure using MCP
   - Initialize tracking files
   - Set up virtual environment
   - Create shared component library

### 2. **NNNNN Development**
   ```
   You: NNNNN
   Claude: ✅ Implemented Module 0001: [Name]
           📁 File: src/[package_name]/core/[file].py
           🔧 MCP Tools: read_file, write_file
           ♻️ Reused: @safe_module (saved 100 tokens)
           📊 Progress: 1/[total] (0.6%)
           💰 Total Tokens Saved: 100 (target: 40%)
           ⏭️ Next: Module 0002
   ```

### 3. **Progress Tracking**
   - Automatic status updates
   - Dependency verification
   - Reusability metrics
   - MCP usage statistics
   - Error documentation

## 📈 NNNNN Progress Example

```
You: NNNNN

Claude: ✅ Implemented Module 0001: [Name]
        📁 File: src/[package_name]/core/[file].py
        🔧 MCP Tools Used: read_file, write_file
        ♻️ Reused Components: @safe_module (saved 100 tokens)
        💾 Token Usage: 285/300
        📊 Progress: 1/[total] (0.6%)
        📈 Total Tokens Saved: 100
        💯 Reusability: 35% (target: 40%)
        ⏭️ Next: Module 0002
```

## 🚀 Result

A complete project with:
- ✅ Professional structure
- ✅ NNNNN automation
- ✅ Progress tracking
- ✅ Error documentation
- ✅ Testing framework
- ✅ Modular architecture (<300 tokens each)
- ✅ MCP integration for all file operations
- ✅ 40%+ code reusability target
- ✅ Token savings tracking
- ✅ Shared component library

---

## 🎯 Key Success Factors

1. **Token Efficiency**
   - Hard limit: 300 tokens per module
   - Use shared components aggressively
   - Track savings in every module

2. **MCP First**
   - Never use standard file operations
   - Always use MCP tools
   - Centralize MCP operations in wrapper

3. **Reusability Metrics**
   - Target: 40% code reuse
   - Extract patterns appearing 3+ times
   - Document token savings

4. **Error Prevention**
   - Centralized error handling
   - MCP wrapper for safe operations
   - Comprehensive error documentation

---

## 📝 Project Structure Overview

```
[PROJECT_NAME]/
├── src/
│   └── [package_name]/
│       ├── __init__.py
│       ├── core/               # Core modules
│       ├── features/           # Feature modules  
│       ├── utils/              # Utility modules
│       └── shared/             # Shared infrastructure
│           ├── error_handler.py
│           ├── mcp_wrapper.py
│           └── validators.py
├── tests/
│   ├── __init__.py
│   ├── conftest.py
│   └── test_*.py              # Module tests
├── _dev/                      # Development tracking
│   ├── module_status.json     # Progress tracking
│   ├── ERROR_GUIDE.md         # Error documentation
│   ├── reusability_tracker.md # Reuse metrics
│   ├── import_map.json        # Import dependencies
│   └── architecture_notes.md  # Design decisions
├── docs/                      # Documentation
├── examples/                  # Usage examples
├── README.md                  # Project overview
├── IMPLEMENTATION_PLAN.md     # Detailed plan
├── MODULE_MAPPING.md          # Module reference
├── PROJECT_INSTRUCTIONS.md    # NNNNN instructions
├── requirements.txt           # Dependencies
├── pyproject.toml            # Project config
└── .gitignore                # Ignore patterns
```

---

END OF TEMPLATE