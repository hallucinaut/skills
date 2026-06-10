---
name: testing
description: "Write unit tests, integration tests, and end-to-end tests. Use when implementing test suites, improving coverage, or ensuring code quality through testing."
---

# Testing Skill

Create comprehensive, maintainable test suites to ensure code reliability and quality.

## When to Use

Use this skill when the user wants to:
- Write unit tests for functions and modules
- Create integration tests for API endpoints
- Implement end-to-end tests with E2E frameworks
- Improve test coverage
- Mock external dependencies
- Set up test environments
- Test database operations, performance, and security

## Testing Strategies

### 1. Unit Testing
- **Focus**: Test individual functions and methods in isolation.
- **Techniques**: Use mocks and stubs for dependencies to avoid side effects.
- **Goal**: High coverage of logic, edge cases, and error conditions.

### 2. Integration Testing
- **Focus**: Test component interactions (e.g., API to Database, Service to Service).
- **Techniques**: Use real (or containerized) databases and mock external third-party APIs.
- **Goal**: Verify data flow and communication between modules.

### 3. End-to-End (E2E) Testing
- **Focus**: Test complete user workflows from the front-end to the back-end.
- **Techniques**: Use tools like Playwright, Cypress, or Puppeteer to simulate browser interactions.
- **Goal**: Ensure the entire system works as expected from the user's perspective.

### 4. Specialized Testing
- **Performance/Load Testing**: Test how the system behaves under heavy load (e.g., JMeter, k6).
- **Security Testing**: Scan for common vulnerabilities like SQLi or XSS (e.g., OWASP ZAP).
- **Contract Testing**: Ensure that API providers and consumers adhere to a shared schema (e.g., Pact).

## Implementation Examples

### Python: Unit Test with `pytest` and `unittest.mock`
```python
import unittest
from unittest.mock import Mock

# The function to test
def get_user_data(api_client, user_id):
    response = api_client.get_user(user_id)
    return response['name']

class TestUserService(unittest.TestCase):
    def test_get_user_data_success(self):
        # Arrange
        mock_client = Mock()
        mock_client.get_user.return_value = {'id': 1, 'name': 'John Doe'}
        
        # Act
        result = get_user_data(mock_client, 1)
        
        # Assert
        self.assertEqual(result, 'John Doe')
        mock_client.get_user.assert_called_once_with(1)

if __name__ == '__main__':
    unittest.main()
```

### JavaScript: Unit Test with `Jest`
```javascript
// math.js
export const add = (a, b) => a + b;

// math.test.js
import { add } from './math';

describe('add function', () => {
  test('adds 1 + 2 to equal 3', () => {
    expect(add(1, 2)).toBe(3);
  });

  test('works with negative numbers', () => {
    expect(add(-1, -1)).toBe(-2);
  });
});
```

## Best Practices

- **AAA Pattern**: Arrange (setup), Act (execute), Assert (verify).
- **Test Independence**: Tests should be able to run in any order and not depend on each other.
- **Fast and Reliable**: Avoid tests that are slow or flaky (non-deterministic).
- **Meaningful Naming**: Test names should clearly describe the scenario and expected outcome.
- **Continuous Integration**: Run your test suite automatically on every pull request.

## Common Pitfalls

- **Testing Implementation Details**: Testing *how* a function works instead of *what* it returns, making refactoring difficult.
- **Ignoring Edge Cases**: Only testing "happy paths" and ignoring null values, empty strings, or large inputs.
- **Slow Test Suites**: Having too many heavy E2E tests in the main development loop, slowing down productivity.
- **Flaky Tests**: Tests that pass sometimes and fail others without any code changes (often due to race conditions).
- **Mocking Too Much**: Creating mocks that are so complex they don't actually reflect real-world behavior.

## Deliverables

- Test suite implementation (Unit, Integration, E2E).
- Test configuration (pytest, Jest, etc.).
- Code coverage reports.
- Test data setup and teardown scripts.
- Mocking/Stubbing utilities.

## Quality Checklist

- [ ] Tests are meaningful and describe the expected behavior.
- [ ] Edge cases (nulls, errors, boundaries) are covered.
- [ ] Tests are fast and do not block the CI pipeline.
- [ ] Setup and teardown are properly handled for each test.
- [ ] Mocks/Stubs are correctly isolated.
- [ ] Tests fail predictably when bugs are introduced.
