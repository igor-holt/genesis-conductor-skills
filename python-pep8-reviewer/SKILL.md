---
name: python-pep8-reviewer
description: Use for reviewing Python code for PEP 8 compliance — check style, naming, whitespace, imports and structure. Activate on requests to review python code, run pep8 check, analyze style, or provide feedback on python snippets and projects.
---

# Python PEP 8 Reviewer

## Overview

This skill provides a structured process for performing thorough code reviews of Python code against the official PEP 8 style guide, identifying violations, explaining issues, and suggesting improvements to enhance readability and consistency.

## Instructions

Follow this process whenever a user provides Python code for review or explicitly requests a PEP 8 style check:

1. **Prepare**: Read the full code snippet or project files provided. If multiple files, review each separately and note cross-file issues like import organization.

2. **Run automated checks if possible**: If in an environment with tools available, use python -m pycodestyle or similar (install via pip only if permitted). Otherwise, perform manual analysis. Report any tool output first.

3. **Structure the response**:
   - Start with an overall score or compliance level (e.g., "Mostly compliant with 5 minor issues").
   - List violations categorized by type.
   - For each violation: quote the offending line(s), explain the PEP 8 rule violated with reference (e.g., "PEP 8 E501: line too long"), suggest fix.
   - End with a revised code example incorporating all fixes where practical.
   - Offer additional best-practice suggestions beyond strict PEP 8 if relevant (e.g., type hints, but flag as extra).

4. **Key PEP 8 checks to perform systematically**:
   - **Line length and wrapping**: Code lines <= 79 characters; comments/docstrings <= 72. Break long lines with parentheses or backslashes. Avoid backslashes for implicit continuation where possible.
   - **Indentation**: Use 4 spaces per level consistently. Never mix tabs and spaces. Align continued lines vertically or use hanging indent.
   - **Naming conventions**:
     - Modules, functions, variables, parameters: lowercase_with_underscores (snake_case).
     - Constants: UPPER_CASE_WITH_UNDERSCORES.
     - Classes and exceptions: CapitalizedWords (CamelCase).
     - Avoid single lowercase letters for variables (except loop vars or comprehensions); use descriptive names.
     - Private names start with single underscore; "dunder" (double underscore) only for special methods.
   - **Imports**:
     - Standard library imports first, then third-party, then local — separated by blank lines.
     - One import statement per line.
     - Use absolute imports; avoid relative imports unless necessary in packages.
     - No `from module import *` (wildcard imports).
     - Group related imports; sort alphabetically within groups when logical.
     - Place imports at the top of the file, after module docstring and before any code.
   - **Whitespace**:
     - No trailing whitespace at end of lines or files.
     - One space after commas, colons (except in slices like list[1:3]), and semicolons.
     - Spaces around arithmetic, comparison, and assignment operators (e.g., a = b + c).
     - No spaces around = in function defaults or keyword arguments (def func(arg=1):).
     - Blank lines: exactly two before top-level function or class definitions; one before method definitions inside classes.
     - Use blank lines sparingly inside functions to separate logical sections.
   - **Comments**:
     - Start with `# ` (hash + space). Use full sentences.
     - Explain *why* rather than *what* the code does.
     - Avoid inline comments for obvious code; place on separate line above if needed.
     - Update comments when code changes.
   - **Docstrings**:
     - Use triple double-quotes `"""` for all public modules, classes, functions, and methods.
     - First line is a one-sentence summary ending with period.
     - Follow with blank line then detailed description if needed.
     - For functions: document parameters, return values, exceptions raised.
     - Use consistent style (e.g., Google, NumPy, or reStructuredText).
   - **Other common rules**:
     - Use `is` and `is not` for comparisons to singletons like None (never `== None`).
     - Use `not in` / `is not` for membership and identity.
     - Avoid unnecessary parentheses in return statements or conditions.
     - Use f-strings for formatting (Python 3.6+); otherwise .format() or %.
     - Ensure consistent quote style (prefer double quotes for strings unless single needed to avoid escapes).
     - Files should end with exactly one newline.

5. **Project-level considerations**:
   - Check for a setup.cfg, pyproject.toml, or .flake8 config that customizes rules (e.g., max line length).
   - Verify __init__.py files in packages.
   - Look for consistent patterns across the codebase (e.g., all functions use type hints or none do).
   - Suggest adding a linter configuration and CI check for ongoing compliance.

6. **Tone and output**: Be constructive and educational. Prioritize high-impact issues (readability, bugs from style) over pedantic ones. If code is clean, affirm good practices and note only optional enhancements.

Always reference specific PEP 8 sections (e.g., "See PEP 8 section 'Whitespace in Expressions and Statements'") when possible. If the code uses modern Python features (walrus operator, match/case), note compatibility with style rules.

This skill does not replace running dedicated linters like flake8 or ruff in production workflows — it complements them with contextual, human-readable analysis.
