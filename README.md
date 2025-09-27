# Grocery Store API Tests

## Overview

This project provides an example framework for running automated API tests for the Grocery Store API using Postman collections and Newman CLI. It supports both end-to-end and data-driven testing, enabling robust validation of API endpoints with dynamic test data.

## Grocery Store API Summary

The Grocery Store API is a simple RESTful service designed for learning and practicing API testing. It provides endpoints to manage products, carts, and orders, allowing users to:
- Retrieve product information
- Create and manage shopping carts
- Add or remove products from carts
- Place orders

Authentication is handled via API keys, and the API supports typical CRUD operations for the main resources.

## Folder Structure

```
postman-cli-datadriven/
│
├── collections/                # Postman collections for E2E and data-driven tests
│   ├── Grocery Store API End-to-End Tests.postman_collection.json
│   └── Grocery Store API DataDriven Tests.postman_collection.json
│
├── envs/                       # Postman environment files
│   └── stage.postman_environment.json
│
├── data/                       # Test data files for data-driven tests
│   ├── products-test-data.json
│   └── carts-test-data.json
│
├── .github/
│   └── workflows/
│       └── postman.yaml        # GitHub Actions workflow for CI
│
└── README.md                   # Project documentation
```

## Environment Variables

- `BASE_URL`: The base URL for the Grocery Store API.
- Other variables (e.g., `cartId`, `productId`) are set dynamically during test execution.

Environment variables are managed via Postman environment files in the `envs/` folder.

## Collections

- **Grocery Store API End-to-End Tests**: Comprehensive tests covering the main API flows.
- **Grocery Store API DataDriven Tests**: Parameterized tests using external data files for products and carts.

## Newman CLI Commands

### Run End-to-End Tests

```sh
newman run "collections/Grocery Store API End-to-End Tests.postman_collection.json" \
  --folder "E2E Tests" \
  -e "envs/stage.postman_environment.json"
```

### Run Data-Driven Product Tests

```sh
newman run "collections/Grocery Store API DataDriven Tests.postman_collection.json" \
  --folder "Products" \
  -d "data/products-test-data.json" \
  -e "envs/stage.postman_environment.json"
```

### Run Data-Driven Cart Tests

```sh
newman run "collections/Grocery Store API DataDriven Tests.postman_collection.json" \
  --folder "Carts" \
  -d "data/carts-test-data.json" \
  -e "envs/stage.postman_environment.json"
```

## Future Plans

- **Reusable Helpers**: Refactor common test logic into reusable helper scripts.
- **Package Migration**: Move utility methods to dedicated Postman packages for better maintainability. Currently Newman does not support Postman packages
- **Secure Secrets Management**: Store API access tokens securely using GitHub Vault or AWS Secrets Manager.
- **Enhanced Reporting**: Integrate advanced reporting tools for test results.
- **CI/CD Integration**: Expand automated workflows for continuous integration and deployment.

---
Feel free to contribute or suggest improvements!