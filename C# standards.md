# C# Coding Standards

## 1. Naming Conventions
- **Classes and Interfaces**:
  - Use `PascalCase` for class and interface names.
  - Prefix interface names with `I`.
  - Example: `CustomerRepository`, `ILogger`
- **Methods**:
  - Use `PascalCase` for method names.
  - Example: `GetCustomer()`, `CalculateTotal()`
- **Variables**:
  - Use `camelCase` for local variables and parameters.
  - Example: `customerName`, `totalAmount`
- **Constants**:
  - Use `PascalCase` for constant names.
  - Example: `MaxRetryCount`, `DefaultTimeout`
- **Private Fields**:
  - Use `_camelCase` with an underscore prefix for private fields.
  - Example: `_userRepository`, `_totalCount`
- **Properties**:
  - Use `PascalCase` for property names.
  - Example: `FirstName`, `IsRegistered`
- **Namespaces**:
  - Use `PascalCase` for namespace names, reflecting the project structure.
  - Example: `Company.Product.Module`

## 2. Code Layout
- **Indentation**:
  - Use 4 spaces per indentation level. Avoid using tabs.
- **Braces**:
  - Place opening braces on the same line as the declaration.
  - Example:
    ```csharp
    if (condition)
    {
        // code
    }
    ```
- **Line Length**:
  - Limit all lines to a maximum of 120 characters.
- **Blank Lines**:
  - Use blank lines to separate logically related blocks of code.
  - Separate class and method definitions with a single blank line.
- **Regions**:
  - Use `#region` and `#endregion` to group related code blocks, but avoid overusing them.

## 3. Commenting
- **XML Documentation**:
  - Use XML documentation comments for all public classes, methods, properties, and fields.
  - Example:
    ```csharp
    /// <summary>
    /// Fetches data from the specified source.
    /// </summary>
    /// <param name="source">The data source to fetch from.</param>
    /// <returns>A task that represents the asynchronous operation.</returns>
    public async Task<Data> FetchDataAsync(string source)
    {
        // Implementation
    }
    ```
- **Inline Comments**:
  - Use inline comments sparingly to explain complex or non-obvious code.
  - Place comments on the line above the code they refer to.
  - Example:
    ```csharp
    // Increment total count
    totalCount++;
    ```

## 4. Error Handling
- Use exceptions for error handling, not return codes.
- Always catch specific exceptions instead of catching the base `Exception` class.
- Example:
  ```csharp
  try
  {
      var data = repository.GetData();
  }
  catch (DataNotFoundException ex)
  {
      Log.Error(ex.Message);
  }
  ```
- Avoid swallowing exceptions; always handle them or log them appropriately.

## 5. Code Structure
- **Methods**:
  - Keep methods short and focused on a single responsibility.
  - Use meaningful names for methods and parameters.
- **Classes**:
  - Follow the Single Responsibility Principle; each class should have one responsibility.
  - Keep classes cohesive and focused.
- **Interfaces**:
  - Prefer small, focused interfaces over large, monolithic ones.
  - Example: `IRepository<T>`, `ILogger`
- **Enums**:
  - Use `PascalCase` for enum names and values.
  - Example:
    ```csharp
    public enum OrderStatus
    {
        Pending,
        Shipped,
        Delivered,
        Cancelled
    }
    ```

## 6. Asynchronous Programming
- Use `async/await` for asynchronous operations.
- Always use `ConfigureAwait(false)` in library code to avoid deadlocks.
- Example:
  ```csharp
  public async Task<Data> GetDataAsync()
  {
      return await repository.GetDataAsync().ConfigureAwait(false);
  }
  ```

## 7. LINQ Usage
- Use LINQ for querying collections, but avoid complex queries that reduce code readability.
- Use method syntax for readability.
- Example:
  ```csharp
  var activeCustomers = customers.Where(c => c.IsActive).ToList();
  ```

## 8. Performance
- Avoid unnecessary object creation, especially in loops.
- Use `StringBuilder` for string concatenations in loops.
- Cache results of expensive operations when possible.
- Prefer `foreach` over `for` loops for iterating collections unless indexing is required.

## 9. Security
- Always validate inputs, especially for public-facing APIs.
- Avoid using `dynamic` where possible to prevent runtime errors.
- Use parameterized queries to prevent SQL injection.
- Secure sensitive data using encryption and other appropriate techniques.

## 10. Unit Testing
- Write unit tests for all critical functionality.
- Use meaningful names for test methods.
- Test method names should follow this pattern: `MethodName_StateUnderTest_ExpectedBehavior`.
  - Example: `CalculateTotal_ValidInput_ReturnsCorrectResult`
- Use mocking frameworks like `Moq` to isolate unit tests.

## 11. Automation & Tools
- **Static Code Analysis**: Use tools like `FxCop` or `StyleCop` to enforce code quality and style standards.
- **Code Formatters**: Use tools like `EditorConfig` or `ReSharper` for consistent code formatting.
- **Build Automation**: Integrate build and deployment tools like `MSBuild`, `Azure DevOps`, or `Jenkins`.

## 12. Continuous Improvement
- Regularly review and update coding standards to align with the latest best practices and project needs.
- Encourage team members to suggest improvements and share knowledge.
