# API Testing Suite: Postman & Newman

![Postman](https://img.shields.io/badge/Postman-v10-FF6C37.svg)
![Newman](https://img.shields.io/badge/Newman-v5.3-green.svg)
![GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-2088FF.svg)

## 📌 Project Overview
This repository contains a fully automated API testing suite built using **Postman** and executed via **Newman**. It serves as a comprehensive example of backend quality assurance, encompassing CRUD operations, environment variables management, and pre-request/test scripts for robust validation.

The target API under exam is the [ReqRes.in](https://reqres.in/) dummy REST API.

## 🏗️ Folder Structure
```
api-testing-postman-newman/
├── collections/
│   └── ReqRes_API_Test_Suite.postman_collection.json
├── environments/
│   └── QA_Environment.postman_environment.json
├── package.json
└── .github/workflows/
    └── newman-tests.yml
```

## 🚀 Tech Stack
- **Tool**: Postman (for script creation)
- **Runner**: Newman (Postman CLI companion)
- **Reporting**: newman-reporter-htmlextra
- **CI/CD**: GitHub Actions

## ⚙️ Local Setup & Installation

To run these API tests locally via CLI, ensure you have [Node.js](https://nodejs.org/) installed.

1. **Clone the repository**:
   ```bash
   git clone https://github.com/talha10/api-testing-postman-newman.git
   cd api-testing-postman-newman
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```
   *This installs Newman and the HTML Extra reporter globally within the project context.*

## 🧪 Execution Commands

- **Run tests (Basic Output)**:
  ```bash
  npm run test
  ```

- **Run tests & generate detailed HTML report**:
  ```bash
  npm run test:report
  ```
  *(The beautiful interactive report will be generated inside an auto-created `newman/` folder).*

## 🛠️ Postman Test Coverage
The `ReqRes_API_Test_Suite` covers:
1. **GET Users**: Pagination parameters, schema validation, response time checks.
2. **GET Single User**: Validates user details matching dynamic IDs, error checks for non-existent users (404).
3. **POST Create User**: Tests payload submission, creates dynamic variables for subsequent requests, 201 status validation.
4. **PUT Update User**: Complete payload update, validates `updatedAt` timestamps.
5. **DELETE User**: Asserts successful deletion returning 204 No Content.

Tests inside Postman utilize `pm.test()`, `pm.expect()`, and `tv4` for JSON Schema validation. Variables like `{{base_url}}` are defined in the `QA_Environment`.

## 🤖 Continuous Integration
Integrated with **GitHub Actions**. Upon any push to the `main` branch, the CI pipeline automatically:
- Provisions an Ubuntu runner.
- Installs Node.js & Newman.
- Executes the Postman Collection utilizing the QA Environment variables.
- Uploads the generated `htmlextra` rich report as a downloadable artifact.

---

## 👤 Author
**Talha Khan** | Senior Software Quality Assurance Engineer  
[LinkedIn](https://www.linkedin.com/in/talha-khan-khattak/) | *Engineered for zero-regression backend deployments.*
