# 🏛️ Indian States REST API (Express.js)

A complete RESTful API built using **Node.js**, **Express.js**, and **CORS** to manage Indian states data including population, literacy rate, annual budget, and GDP.

This project demonstrates proper REST architecture, CRUD operations, route parameters, validation logic, PUT vs PATCH differences, sorting, and filtering — all using in-memory storage.

---

## 📌 Tech Stack

- Node.js  
- Express.js  
- CORS  
- JSON (In-memory array storage)

---

## 📂 Project Structure

```
project-folder/
│
├── server.js
├── package.json
└── README.md
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repository

```bash
git clone <your-repo-url>
cd project-folder
```

### 2️⃣ Install Dependencies

```bash
npm install express cors
```

### 3️⃣ Run Server

```bash
node server.js
```

Server runs at:

```
http://localhost:3000
```

---

# 📊 Data Structure

Each state object follows this structure:

```json
{
  "id": 1,
  "name": "Andhra Pradesh",
  "population": 49386799,
  "literacyRate": 67.02,
  "annualBudget": 279279,
  "gdp": 14000000
}
```

---

# 🌐 API Endpoints

---

## 🔹 Root Route

### `GET /`

Checks server status.

Response:
```json
{
  "message": "Sever is Running"
}
```

---

# 📖 READ OPERATIONS

---

## 🔹 Get All States

### `GET /states`

Returns full states array.

---

## 🔹 Get State By ID

### `GET /states/:id`

Example:
```
GET /states/5
```

Errors:
- 400 → Invalid ID
- 404 → State Not Found

---

## 🔹 Get States Sorted by Highest GDP

### `GET /states/highest-gdp`

Returns states sorted in descending GDP order.

---

# ➕ CREATE OPERATION

---

## 🔹 Add New State

### `POST /states`

All fields required.

Example Request Body:
```json
{
  "name": "New State",
  "population": 1000000,
  "literacyRate": 75,
  "annualBudget": 50000,
  "gdp": 2000000
}
```

Response:
```json
{
  "state": { ... }
}
```

Validation:
- All fields mandatory
- Numeric fields must be numbers

---

# 🔄 UPDATE OPERATIONS (PUT)

PUT replaces entire object.

---

## 🔹 Full Update

### `PUT /states/:id`

All fields required.

If any field missing → 400 error.

---

## 🔹 Update Only Budget

### `PUT /states/:id/budget`

```json
{
  "annualBudget": 300000
}
```

---

## 🔹 Update Only Population

### `PUT /states/:id/population`

```json
{
  "population": 5000000
}
```

---

# ✏️ PARTIAL UPDATE (PATCH)

PATCH updates specific fields only.

---

## 🔹 Update Literacy Rate

### `PATCH /states/:id/literacy`

Validation:
- Must be number
- Must be between 0 and 100

---

## 🔹 Update GDP

### `PATCH /states/:id/gdp`

Validation:
- Must be number

---

## 🔹 General Partial Update

### `PATCH /states/:id`

Allowed fields:
- name
- population
- literacyRate
- annualBudget
- gdp

Example:
```json
{
  "annualBudget": 280000
}
```

Rules:
- Only allowed fields accepted
- Numeric fields must be numbers
- literacyRate must be 0–100
- Empty body rejected

---

# ❌ DELETE OPERATIONS

---

## 🔹 Delete By ID

### `DELETE /states/:id`

Returns:
- 204 No Content (success)
- 400 Invalid Input
- 404 State Not Found

---

## 🔹 Delete By Name

### `DELETE /states/name/:stateName`

Case-insensitive matching.

---

## 🔹 Delete States Below Literacy Percentage

### `DELETE /states/low-literacy/:percentage`

Example:
```
DELETE /states/low-literacy/70
```

Deletes states having literacy rate lower than given percentage.

Response:
```json
{
  "deletedCount": 3
}
```

Validation:
- Percentage must be between 0–100

---

# 🧠 Validation Rules

- ID must be numeric
- Required fields enforced in POST and PUT
- PATCH only allows predefined fields
- Numeric fields strictly validated
- literacyRate range: 0–100
- Invalid field names rejected
- Empty update body rejected

---

# 🚨 Important Notes

- Data is stored in memory (array)
- Restarting server resets data
- No database connected
- No authentication
- No pagination
- No rate limiting

---

# 🔥 Possible Improvements

To make this production-ready:

- Add MongoDB or PostgreSQL
- Implement MVC architecture
- Add pagination & filtering
- Add authentication (JWT)
- Add middleware logging
- Add rate limiting
- Add Swagger API documentation
- Add environment variables
- Add centralized error handler
- Add unit tests

---

# 🧪 Testing Tools

You can test API using:

- Postman
- Thunder Client
- curl
- REST Client extension

---

# 📌 HTTP Status Codes Used

| Code | Meaning |
|------|---------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 404 | Not Found |

---

# 🎯 Learning Outcomes

By building this project, you understand:

- Express routing
- Middleware usage
- REST API design
- CRUD operations
- PUT vs PATCH difference
- Input validation logic
- Sorting & filtering arrays
- HTTP status handling

---

# 👨‍💻 Author

Backend practice project using Express.js.

---

# 🚀 Server URL

```
http://localhost:3000
```

---

This project is suitable for backend beginners learning REST API fundamentals and Express.js architecture.
