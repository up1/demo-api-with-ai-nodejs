---
name: bruno-api-test
description: Generate test cases for API endpoints using Bruno
---

## Workflow of Bruno API Test Skill
1. Read the API specification and understand the endpoints, request/response formats, and status codes from user's requirement
2. Create or update Bruno request and test cases in `api-testing/` for each endpoint, covering success and error scenarios (separately) follow from best practices.
   * Response testing with Bruno: https://docs.usebruno.com/testing/script/response/response-object)
3. Run the Bruno test collection with bruno cli and verify the results.
   * Start server before running the tests.
4. Report back the test results, including any failures and their details.

## Project or collection structure of Bruno tests
```
api-testing/
├── opencollection.yml
├── feature_name_testcase_name_200.yml
├── feature_name_testcase_name_400.yml
├── feature_name_testcase_name_201.yml
├── feature_name_testcase_name_404.yml
├── feature_name_testcase_name_500.yml
└── README.md
```

## Best Practices
- Don't hard code URL of the API server; use environment variables or configuration files instead.
- Organize test cases by feature and scenario for better maintainability.
- Cover both success and error scenarios for each endpoint.
- Keep test cases independent and idempotent to avoid side effects.
- Use descriptive names for test case files to clearly indicate the feature and scenario being tested.
- Keep the test cases up-to-date with any changes in the API specification.
- Review and refactor test cases periodically to maintain quality and relevance.