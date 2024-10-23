# Personal Expense Tracker

## Overview

This project is a **Personal Expense Tracker** API, allowing users to manage their financial records effectively. Users can record their income and expenses, retrieve past transactions, and get summaries by category or time period.

## Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: SQLite (or MongoDB)
- **API Testing**: Thunder Client (VS Code extension)

## Database Setup

### Using SQLite
The database contains the following tables:

- **transactions**: Handles all financial records.
  - Fields: `id`, `type` (income/expense), `category`, `amount`, `date`, `description`.
- **categories**: Stores categories for transactions.
  - Fields: `id`, `name`, `type` (income/expense).

### Using MongoDB
The database contains the following collections:

- **transactions**: Manages user transactions.
  - Fields: `type`, `category`, `amount`, `date`, `description`.
- **categories**: Defines categories for classification.
  - Fields: `name`, `type`.

## API Endpoints

### 1. **Create a New Transaction**
   - **Endpoint**: `POST /transactions`
   - **Description**: Add a new income or expense transaction.
   - **Request Body**:
     ```json
     {
       "type": "income or expense",
       "category": "category name",
       "amount": 1000,
       "date": "YYYY-MM-DD",
       "description": "Transaction details"
     }
     ```
   - **Response**:
     ```json
     {
       "id": 1,
       "type": "income",
       "category": "Salary",
       "amount": 1000,
       "date": "2024-10-01",
       "description": "October salary"
     }
     ```

### 2. **Retrieve All Transactions**
   - **Endpoint**: `GET /transactions`
   - **Description**: Fetch all transactions.
   - **Response**:
     ```json
     [
       {
         "id": 1,
         "type": "income",
         "category": "Salary",
         "amount": 1000,
         "date": "2024-10-01",
         "description": "October salary"
       },
       {
         "id": 2,
         "type": "expense",
         "category": "Groceries",
         "amount": 200,
         "date": "2024-10-02",
         "description": "Weekly grocery shopping"
       }
     ]
     ```

### 3. **Retrieve a Transaction by ID**
   - **Endpoint**: `GET /transactions/:id`
   - **Description**: Fetch a single transaction by its unique ID.
   - **Response**:
     ```json
     {
       "id": 1,
       "type": "income",
       "category": "Salary",
       "amount": 1000,
       "date": "2024-10-01",
       "description": "October salary"
     }
     ```

### 4. **Update a Transaction**
   - **Endpoint**: `PUT /transactions/:id`
   - **Description**: Update the details of an existing transaction by ID.
   - **Request Body**:
     ```json
     {
       "type": "income",
       "category": "Salary",
       "amount": 1500,
       "date": "2024-10-01",
       "description": "October full salary"
     }
     ```
   - **Response**:
     ```json
     {
       "id": 1,
       "type": "income",
       "category": "Salary",
       "amount": 1500,
       "date": "2024-10-01",
       "description": "October full salary"
     }
     ```

### 5. **Delete a Transaction**
   - **Endpoint**: `DELETE /transactions/:id`
   - **Description**: Remove a transaction by ID.
   - **Response**:
     ```json
     {
       "message": "Transaction deleted successfully"
     }
     ```

### 6. **Retrieve Summary of Transactions**
   - **Endpoint**: `GET /summary`
   - **Description**: Get a summary of transactions including total income, total expenses, and balance.
   - **Query Parameters (optional)**: `?startDate=YYYY-MM-DD&endDate=YYYY-MM-DD&category=categoryName`
   - **Response**:
     ```json
     {
       "totalIncome": 5000,
       "totalExpenses": 1200,
       "balance": 3800
     }
     ```

## Setup and Installation

1. **Clone the Repository**:
   ```bash
   git clone <https://github.com/RabbanMehamood/floww-ai.git>
   cd <floww-ai>

2.  **Database Setup**:
    - using SQLite, the database file will be created automatically when the server runs.

3. **Start the server**:
    ```bash
    node app.js

4. **Open thunder client, or postman and do API testing.

