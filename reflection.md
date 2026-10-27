# Reflection

**Note:** The supplied three-page Lab 5 handout refers to reflection questions but does not include the actual question wording. The responses below address the learning outcomes and reflection topic stated in the handout.

### 1. What is static code analysis, and why is it useful?

Static code analysis checks source code without running the application. It helps identify likely bugs, unsafe coding patterns, and style problems early, making code easier to review and maintain.

### 2. What did Pylint, Bandit, and Flake8 each contribute?

Pylint focuses on code quality and potential programming mistakes. Bandit highlights common security risks, such as unsafe YAML loading and debug configuration. Flake8 checks formatting and PEP 8 conventions, including whitespace and line length. They overlap in some areas but serve different purposes.

### 3. Which issues were most important, and how were they fixed?

Security-related issues were prioritized: unsafe YAML parsing, a hard-coded password, a remote logging configuration listener, HTML injection risk, and debug mode. Functional defects were also fixed, including the capacity boundary, gender compatibility, duplicate allocation, and stale room occupancy after vacating.

### 4. What did you learn, and what are the limitations of static analysis?

The tools help catch problems that can be missed during ordinary reading, but they cannot prove that the program behaves correctly in every situation. The application still needs runtime tests and manual review. Static analysis should be part of development, not a replacement for testing.
