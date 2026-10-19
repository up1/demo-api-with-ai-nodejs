---
name: api-nodejs-dev
description: REST API development using Node.js + express and sqlite database and testing with jest and supertest libraries
---

## Workflow of API Development with Node.js
1. Analyze the requirements and work breakdown tasks from user's requirements.
2. Implement the API endpoints using Node.js and Express framework that follow NodeJS best practices and project structure`
3. Integrate the API with a sqlite database for data persistence.
4. Write tests for the API endpoints using jest and supertest libraries.
5. Run the tests and ensure all endpoints work as expected.
   * If tests fail, debug the issues and fix the API implementation accordingly.


## Technologies Stack
- Node.js
- Express
- sqlite with built-in support in Node.js(https://nodejs.org/api/sqlite.html)
  * Don't use any external sqlite libraries.
- Unit test and integration with jest and supertest
  * Unit test for service layer only
  * Integration test for controller layer only

## Project Structure with feature-based organization
```
.
├── src
│   ├── features
│   │   ├── feature1
│   │   │   ├── controllers.js
│   │   │   ├── models.js
│   │   │   ├── routes.js
│   │   │   └── services.js
│   ├── middlewares
│   │   └── middlewares.js
│   ├── utils
│   │   └── utils.js
│   └── app.js
├── tests
│   ├── feature1_controllers_success.test.js
│   ├── feature1_controllers_failure.test.js
│   ├── feature1_services_success.test.js
│   ├── feature1_services_failure.test.js
├── package.json
└── README.md
```

## Best Practices
- Must try to create a new file instead of modifying existing ones.
- Keep the service layer and controller layer separate.
- Don't write comments in the code; rely on clear and self-explanatory code instead.
- Write unit tests for the service layer and integration tests for the controller layer.
- Use async/await for asynchronous operations.
- Handle errors gracefully and return appropriate HTTP status codes.
- Avoid using any external sqlite libraries; use the built-in support in Node.js.
- Keep the code modular and reusable.
- Follow consistent naming conventions for files and directories.
