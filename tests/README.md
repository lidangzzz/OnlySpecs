# Tests

This directory contains test suites for the OnlyFans application.

## Claude SDK Tests

The `claude-sdk.test.ts` file tests the Claude Agent SDK integration.

### Running Tests

#### Mock Mode (No API calls)
```bash
npm run test:mock
```
This runs basic functionality tests without making any API calls. Safe to run without credentials.

#### Live Mode (Real API calls)
```bash
export CLAUDE_API_KEY="your-api-key"
export CLAUDE_BASE_URL="https://api.anthropic.com"  # Optional, defaults to this
npm run test
```
This runs tests that make actual API calls to Claude. Requires valid credentials.

### Test Coverage

The test suite covers:

1. **SDK Initialization**
   - Creating SDK instances
   - Verifying method existence

2. **Configuration Validation**
   - Valid configurations
   - Missing API key detection
   - Missing base URL detection

3. **Query Execution** (Live mode only)
   - Real API calls
   - Progress callback functionality
   - Response parsing

4. **Error Handling**
   - Invalid credentials
   - Network errors
   - Malformed responses

### Adding New Tests

To add new tests:

1. Add a new test section in `runTests()` function
2. Use the helper functions:
   - `logTest(testName)` - Start a new test section
   - `recordTest(name, passed, error)` - Record test result
   - `logPass(message)` - Log pass message
   - `logFail(message, error)` - Log fail message
   - `logInfo(message)` - Log info message

Example:
```typescript
logTest('My New Test');
try {
  const result = myFunction();
  recordTest('Function returns expected result', result === expected);
} catch (error: any) {
  recordTest('My New Test', false, error.message);
}
```
