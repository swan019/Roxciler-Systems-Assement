# MERN Stack Transactions Platform

This project is a MERN stack application that allows users to interact with product transactions, including viewing transactions, searching, paginating, and visualizing data through charts. It fetches data from a third-party API and displays statistics like total sales and item categories.

## Table of Contents

- [Overview](#overview)
- [Technologies Used](#technologies-used)
- [Backend Approach](#backend-approach)
- [Frontend Approach](#frontend-approach)
- [API Routes](#api-routes)
- [Setup and Running the Project](#setup-and-running-the-project)

## Overview

This platform offers:
1. Listing transactions with search and pagination functionality.
2. Displaying statistics like total sales and sold/unsold items for a selected month.
3. Bar chart showing the price range and item distribution.
4. Pie chart showing the categories of products sold.

The data is fetched from a third-party API and stored in MongoDB, allowing efficient data retrieval and processing through various APIs.

---

## Technologies Used

### **Frontend**:
- **React**: For building the user interface.
- **Ant Design**: Provides pre-built components like tables, forms, and buttons for a sleek UI.
- **Chart.js**: For rendering dynamic charts like bar and pie charts.
- **Moment.js**: To handle date formatting and manipulation.
- **Axios**: For making HTTP requests from the frontend to the backend API.

### **Backend**:
- **Express**: Web framework for building RESTful APIs.
- **Node.js**: JavaScript runtime to execute server-side code.
- **Mongoose**: ORM for MongoDB to define schemas and interact with the database.
- **MongoDB**: NoSQL database to store and retrieve transactions.
- **Axios**: Used in the backend to fetch the third-party data and seed the database.

---

## Backend Approach

1. **Data Fetching & Initialization**:
   - Used `Axios` to fetch transaction data from the [Third-party API](https://s3.amazonaws.com/roxiler.com/product_transaction.json) and store it in MongoDB using Mongoose models.
   - Initialized the database with proper collection structures to efficiently store data related to product transactions.

2. **Data Handling**:
   - Implemented APIs to process transactions for a specific month (irrespective of the year) and return results for:
     - Listing all transactions with pagination.
     - Calculating total sales, total sold, and unsold items.
     - Generating bar charts based on price ranges.
     - Generating pie charts based on product categories.

---

## Frontend Approach

1. **UI Layout**:
   - Used Ant Design for building a user-friendly UI, including tables, dropdowns, and buttons.
   - The month dropdown allows users to filter data, with March selected by default.

2. **Charts & Data Visualization**:
   - Utilized `Chart.js` to generate dynamic bar and pie charts based on the data returned from the APIs.

3. **Data Interaction**:
   - Integrated `Axios` to fetch data from the backend and update the frontend dynamically as the user interacts with the UI (e.g., searching, changing pages, selecting months).

---

## API Routes

### **GET /api/initialize**
- **Description**: Fetch data from the third-party API and initialize the database.
- **Response**: Initializes the MongoDB with product transactions.

### **GET /api/transactions**
- **Parameters**: 
  - `month`: The selected month (January - December).
  - `search`: (optional) Search query for product title, description, or price.
  - `page`: (optional) Pagination page number.
  - `per_page`: (optional) Number of results per page (default is 10).
- **Response**: Lists all transactions for the selected month, with search and pagination support.

### **GET /api/statistics**
- **Parameters**: 
  - `month`: The selected month.
- **Response**: Returns total sales amount, total sold items, and total unsold items for the selected month.

### **GET /api/bar-chart**
- **Parameters**: 
  - `month`: The selected month.
- **Response**: Returns price ranges and the number of items in each range for the selected month.

### **GET /api/pie-chart**
- **Parameters**: 
  - `month`: The selected month.
- **Response**: Returns the product categories and the number of items in each category for the selected month.

### **GET /api/combined**
- **Parameters**: 
  - `month`: The selected month.
- **Response**: Combines the responses of the above APIs (transactions, statistics, bar chart, pie chart) into a single JSON response.

---

## Setup and Running the Project

### **1. Clone the Repository**
```bash
git clone <repository-url>
cd project-directory

```
### **2. Install Dependencies**
```bash
# Backend dependencies
cd backend
npm install

# Frontend dependencies
cd frontend
npm install

```

### **3. Environment Variables**
 ```bash
  MONGO_URI=mongodb://localhost:27017/Roxiller-Task
  PORT=5000
  ```

### **4. Run the Application**
- **Backend: Start the backend server:**
    ```bash
    cd server
    npm start
    ```
- **Frontend: Start the frontend server:**
    ```bash
    cd client
    npm start
    ```

## Visit http://localhost:3000 to view the application.



