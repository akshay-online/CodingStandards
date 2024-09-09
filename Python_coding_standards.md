# Python Coding Standards

## 1. Naming Conventions
- **Variables**: Use `snake_case` for variable names.
  - Example: `user_name`, `total_count`
- **Functions**: Use `snake_case` for function names.
  - Example: `calculate_total()`, `get_user_input()`
- **Classes**: Use `PascalCase` for class names.
  - Example: `UserProfile`, `DataProcessor`
- **Constants**: Use `ALL_CAPS_WITH_UNDERSCORES` for constant names.
  - Example: `MAX_RETRIES`, `DEFAULT_TIMEOUT`
- **Modules/Packages**: Use `snake_case` for module and package names.
  - Example: `data_processor.py`, `user_profile.py`

## 2. Code Layout
- **Indentation**: Use 4 spaces per indentation level. Avoid using tabs.
- **Line Length**: Limit all lines to a maximum of 79 characters.
- **Blank Lines**:
  - Separate top-level function and class definitions with two blank lines.
  - Separate method definitions inside a class with a single blank line.
- **Imports**:
  - Imports should usually be on separate lines.
  - Group imports in the following order:
    1. Standard library imports.
    2. Related third-party imports.
    3. Local application/library-specific imports.
  - Example:
    ```python
    import os
    import sys

    import requests

    from myapp import mymodule
    ```
- **Whitespace**:
  - Avoid extra spaces inside parentheses, brackets, or braces.
  - Use a single space around operators and after commas.
  - Do not use spaces around the `=` sign when used to indicate a keyword argument or a default parameter value.

## 3. Commenting
- **Docstrings**:
  - Use triple quotes `"""` for all docstrings (single-line or multi-line).
  - All public modules, functions, classes, and methods should have docstrings.
  - Example:
    ```python
    def fetch_data(url):
        """Fetch data from the specified URL.

        Args:
            url (str): The URL to fetch data from.

        Returns:
            dict: Parsed JSON data from the response.
        """
        pass
    ```
- **Inline Comments**:
  - Use inline comments sparingly and only to explain complex logic.
  - Place inline comments on the same line as the code they refer to, separated by at least two spaces.
  - Example:
    ```python
    x = x + 1  # Increment x by 1
    ```

## 4. Error Handling
- Always use specific exceptions rather than bare `except` clauses.
- Example:
  ```python
  try:
      result = some_function()
  except ValueError as e:
      handle_value_error(e)
  ```
- Use `finally` for cleanup actions that must be executed under all circumstances.

## 5. Code Structure
- **Functions**:
  - Keep functions small and focused on a single task.
  - Use meaningful names for functions and parameters.
- **Classes**:
  - Follow the Single Responsibility Principle; each class should have one responsibility.
  - Use class methods for functionality related to the class that doesn’t need an instance.
- **Modules**:
  - Group related functions and classes together.
  - Avoid placing too much code in a single module; break it up if it becomes too large.

## 6. Testing
- Write unit tests for all public functions and classes.
- Use meaningful names for test functions.
- Test names should follow this pattern: `test_<functionality_under_test>`.
  - Example: `test_user_creation()`
- Use assertions effectively to validate the behavior of code.

## 7. Performance
- Avoid unnecessary loops and list comprehensions that may affect performance.
- Prefer built-in functions and libraries over manually implemented solutions.
- Use generators where possible to handle large data sets.

## 8. Security
- Validate all inputs, especially if they come from untrusted sources.
- Avoid using `eval()` or `exec()` with untrusted data.
- Always use parameterized queries for database access to prevent SQL injection.
- Store secrets and sensitive information securely (e.g., environment variables).

## 9. Automation & Tools
- **Linters**: Use tools like `flake8` or `pylint` to enforce code quality and style standards.
- **Code Formatters**: Use `black` for consistent code formatting.
- **Type Checking**: Use `mypy` for static type checking.
- **Testing**: Use `pytest` for writing and running tests.

## 10. Continuous Improvement
- Regularly review and update coding standards to align with the latest best practices and project needs.
- Encourage team members to suggest improvements and share knowledge.
```
