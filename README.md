# Postman + Newman + GitHub Actions = Task 6

## Project Overview
This project demonstrates API testing using **Postman**, **Newman**, and **GitHub Actions**.  
It is based on a simple store API that supports CRUD operations for products, users, and orders.  
The project also includes CI automation to run Newman tests and publish the generated HTML report to **GitHub Pages**.

---

## Technologies Used
- **Node.js**  
- **Postman / Newman**  
- **GitHub Actions**  
- **Express.js** (local testing API)

---

## Setup and Run Locally

### 1. Clone the repository
```bash
git clone https://github.com/alinapurtova/postman_newman_task6.git
cd postman_newman_task6
```
### 2. Install dependencies
```bash
npm i
```
### 3. Run local API server
```bash
npm run turn-on-api
```

### 4. Test API manually
You can check the available routes in the browser or via Postman:

| VERB     |Route          | Input      | Output             |
|----------|---------------|------------|--------------------|
| GET      | /products     | *None*     | **Array**          |
| GET      | /products/:id |  **e.g 3** | **Object**         |
| POST     | /products     | **object** | **Created object** |
| PUT      | /products     | **object** | **Updated object** |
| DELETE   | /products/:id | **e.g 3**  | **Deleted object** |

Similar routes are available for /users and /orders.

## Postman Testing

### 1. Import collection
Open **Postman** and import the file:
store.postman_collection.json

### 2. Run and review tests
Run the requests and check the tests that verify:

+ Status codes (200, 400, etc.)  
+ Response time  
+ Pagination & sorting (using query params)  
+ JSON Schema validation  
+ AAA approach (Arrange - Act - Assert)

---

## Running Tests via Newman

Run the Postman collection with **Newman**:
```bash
npm run test-newman
```

The test results will be generated as an **HTML report**, saved to reports/index.html.

## GitHub Actions Integration

This project includes a **GitHub Actions** workflow that:

- Runs Newman tests automatically on push to the main branch  
- Generates an HTML report  
- Pushes it to the `newman-report` branch  
- Publishes the result to **GitHub Pages**