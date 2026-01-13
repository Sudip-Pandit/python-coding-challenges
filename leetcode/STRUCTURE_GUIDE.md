# Repository Structure and Organization Guide

Complete directory structure for the Python Coding Challenges repository.

---

## 📁 Recommended Directory Structure

```
python-coding-challenges/
│
├── README.md                          # Main repository overview
├── CONTRIBUTING.md                     # Contribution guidelines
├── LICENSE                            # MIT License
│
├── 01_Fundamentals/
│   ├── README.md                      # Fundamentals overview
│   ├── fundamentals_challenges.md     # 30 fundamental problems
│   ├── solutions/
│   │   ├── problem_01_variable_swap.py
│   │   ├── problem_02_type_conversion.py
│   │   └── ... (all solution files)
│   └── tests/
│       ├── test_problem_01.py
│       └── ... (all test files)
│
├── 02_Data_Structures/
│   ├── README.md                      # Data structures overview
│   ├── lists/
│   │   ├── lists_challenges.md        # 25 list problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── tuples/
│   │   ├── tuples_challenges.md       # 15 tuple problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── sets/
│   │   ├── sets_challenges.md         # 20 set problems
│   │   ├── solutions/
│   │   └── tests/
│   └── dictionaries/
│       ├── dictionaries_challenges.md  # 40 dictionary problems
│       ├── solutions/
│       └── tests/
│
├── 03_Functions/
│   ├── README.md                      # Functions overview
│   ├── basic_functions/
│   │   ├── basic_challenges.md        # 20 basic problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── lambda_functions/
│   │   ├── lambda_challenges.md       # 10 lambda problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── higher_order_functions/
│   │   ├── hof_challenges.md          # 15 HOF problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── recursion/
│   │   ├── recursion_challenges.md    # 15 recursion problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── decorators/
│   │   ├── decorator_challenges.md    # 10 decorator problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── generators/
│   │   ├── generator_challenges.md    # 10 generator problems
│   │   ├── solutions/
│   │   └── tests/
│   └── advanced/
│       ├── advanced_challenges.md     # 20 advanced problems
│       ├── solutions/
│       └── tests/
│
├── 04_OOP/
│   ├── README.md                      # OOP overview
│   ├── classes_and_objects/
│   │   ├── basics_challenges.md       # 15 basic problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── inheritance/
│   │   ├── inheritance_challenges.md  # 15 inheritance problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── polymorphism/
│   │   ├── polymorphism_challenges.md # 10 polymorphism problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── encapsulation/
│   │   ├── encapsulation_challenges.md # 10 encapsulation problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── magic_methods/
│   │   ├── magic_methods_challenges.md # 15 magic methods problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── class_methods/
│   │   ├── methods_challenges.md      # 10 methods problems
│   │   ├── solutions/
│   │   └── tests/
│   └── design_patterns/
│       ├── patterns_challenges.md     # 25 design pattern problems
│       ├── solutions/
│       └── tests/
│
├── 05_Algorithms/
│   ├── README.md                      # Algorithms overview
│   ├── searching/
│   │   ├── searching_challenges.md
│   │   ├── solutions/
│   │   └── tests/
│   ├── sorting/
│   │   ├── sorting_challenges.md
│   │   ├── solutions/
│   │   └── tests/
│   ├── string_algorithms/
│   │   ├── string_challenges.md
│   │   ├── solutions/
│   │   └── tests/
│   └── mathematical/
│       ├── math_challenges.md
│       ├── solutions/
│       └── tests/
│
├── 06_Interview_Prep/
│   ├── README.md                      # Interview prep overview
│   ├── easy/
│   │   ├── easy_problems.md           # 30 easy problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── medium/
│   │   ├── medium_problems.md         # 50 medium problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── hard/
│   │   ├── hard_problems.md           # 20 hard problems
│   │   ├── solutions/
│   │   └── tests/
│   ├── patterns/
│   │   ├── common_patterns.md
│   │   └── pattern_examples/
│   └── company_specific/
│       ├── faang_problems.md
│       └── other_companies/
│
├── resources/
│   ├── cheat_sheets/
│   │   ├── python_basics_cheatsheet.md
│   │   ├── data_structures_cheatsheet.md
│   │   ├── algorithms_cheatsheet.md
│   │   └── time_complexity_guide.md
│   ├── best_practices/
│   │   ├── coding_style.md
│   │   ├── documentation.md
│   │   └── testing_guide.md
│   └── learning_paths/
│       ├── beginner_path.md
│       ├── intermediate_path.md
│       └── advanced_path.md
│
├── utils/
│   ├── test_runner.py                 # Automated test runner
│   ├── progress_tracker.py            # Track your progress
│   └── solution_template.py           # Template for solutions
│
└── .github/
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.md
    │   └── feature_request.md
    └── workflows/
        └── tests.yml                  # CI/CD for automated testing
```

---

## 📝 File Naming Conventions

### Challenge Files
- Use descriptive names: `data_type_challenges.md`
- Separate words with underscores
- Include difficulty in filename if needed: `advanced_oop_challenges.md`

### Solution Files
- Match problem numbers: `problem_01_variable_swap.py`
- Include problem name for clarity
- Format: `problem_XX_description.py`

### Test Files
- Mirror solution structure: `test_problem_01.py`
- Use `test_` prefix for pytest compatibility

---

## 📄 Standard File Templates

### Challenge File Template
```markdown
# [Topic Name] - Coding Challenges

Brief description of the topic.

---

## Problem X: [Problem Title]
**Difficulty**: Easy/Medium/Hard

**Problem**: Clear problem statement

**Input**: Example input
**Output**: Expected output

**Constraints**:
- Constraint 1
- Constraint 2

**Solution**:
```python
# Solution code here
```

**Explanation**: How the solution works

**Time Complexity**: O(?)
**Space Complexity**: O(?)
```

### Solution File Template
```python
"""
Problem X: [Problem Title]
Difficulty: Easy/Medium/Hard

Problem Statement:
[Brief description]

Author: [Your Name]
Date: [Date]
"""

def solution_function(params):
    """
    [Brief description of what function does]
    
    Args:
        param1: Description
        param2: Description
    
    Returns:
        Description of return value
    
    Time Complexity: O(?)
    Space Complexity: O(?)
    """
    # Implementation
    pass


def main():
    """Test cases"""
    # Test case 1
    # Test case 2
    # etc.


if __name__ == "__main__":
    main()
```

### Test File Template
```python
"""
Tests for Problem X: [Problem Title]
"""

import pytest
from solutions.problem_XX import solution_function


class TestProblemXX:
    """Test cases for Problem XX"""
    
    def test_basic_case(self):
        """Test basic functionality"""
        assert solution_function(input) == expected_output
    
    def test_edge_case_1(self):
        """Test edge case 1"""
        assert solution_function(edge_input) == expected_output
    
    def test_edge_case_2(self):
        """Test edge case 2"""
        assert solution_function(edge_input) == expected_output
    
    def test_invalid_input(self):
        """Test invalid input handling"""
        with pytest.raises(ValueError):
            solution_function(invalid_input)
```

---

## 🎯 Organization Best Practices

### 1. Consistent Structure
- Every topic folder has the same structure
- Solutions always in `/solutions` subfolder
- Tests always in `/tests` subfolder

### 2. Progressive Difficulty
- Easy problems first
- Gradually increase complexity
- Mark difficulty clearly

### 3. Comprehensive Documentation
- Each folder has a README
- Clear problem statements
- Well-commented solutions

### 4. Version Control
- Use meaningful commit messages
- One problem per commit (optional)
- Tag major milestones

### 5. Testing
- Write tests for all solutions
- Use pytest framework
- Aim for 100% test coverage

---

## 🔧 Setup Instructions

### For Contributors
```bash
# Clone the repository
git clone https://github.com/Sudip-Pandit/python-coding-challenges.git
cd python-coding-challenges

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run tests
pytest

# Run specific test file
pytest tests/test_problem_01.py
```

### For Learners
```bash
# Navigate to topic of interest
cd 01_Fundamentals

# Read challenges
cat fundamentals_challenges.md

# Try solving without looking at solutions
# When ready, check solutions
cat solutions/problem_01_variable_swap.py

# Run tests to verify understanding
pytest tests/test_problem_01.py
```

---

## 📊 Progress Tracking

### Using the Progress Tracker
```python
# Track your progress
python utils/progress_tracker.py

# Mark problem as completed
python utils/progress_tracker.py --complete 01_Fundamentals/problem_01

# View statistics
python utils/progress_tracker.py --stats
```

---

## 🤝 Contributing Guidelines

1. **Pick an Issue**: Check open issues or create new one
2. **Fork Repository**: Create your own copy
3. **Create Branch**: `git checkout -b feature/your-feature`
4. **Write Code**: Follow style guide
5. **Write Tests**: Ensure tests pass
6. **Submit PR**: Clear description of changes

---

## 📚 Additional Resources

### In Repository
- Cheat sheets in `/resources/cheat_sheets`
- Learning paths in `/resources/learning_paths`
- Best practices in `/resources/best_practices`

### External Resources
- Python Documentation: https://docs.python.org
- PEP 8 Style Guide: https://pep8.org
- Real Python: https://realpython.com

---

## 🎓 Suggested Learning Order

1. **Week 1-2**: Fundamentals
2. **Week 3-4**: Data Structures
3. **Week 5**: Functions
4. **Week 6-7**: OOP
5. **Week 8-10**: Algorithms
6. **Ongoing**: Interview Prep

---

**Happy Organizing! 🐍**
