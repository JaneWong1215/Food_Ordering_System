# Food Ordering & Customer Membership Database System

A comprehensive, end-to-end relational database system designed to manage food ordering operations, staff hierarchal organization, and customer membership tracking. This system covers the full lifecycle of database engineering, from conceptual ER/EER modeling to physical script schema creation and advanced PL/SQL programming.

---

## 📖 Table of Contents
1. [Project Overview](#project-overview)
2. [Database Scope & Business Rules](#database-scope--business-rules)
3. [Schema Architecture & Data Dictionary](#schema-architecture--data-dictionary)
4. [Advanced PL/SQL Programming](#advanced-plsql-programming)
5. [Contributors](#contributors)

---

## 🎯 Project Overview
This database system bridges food ordering workflows and historical membership tracking for a dynamic restaurant model. Designed in **Oracle SQL**, it uses specialized data models like Enhanced Entity-Relationship (EER) modeling to support subtyping (such as managing different Employee structures and customer guest/member roles).

---

## ⚙️ Database Scope & Business Rules

The system logic strictly enforces the following real-world operational guidelines:
* **Customers & Orders:** Each customer can place multiple orders over time. An order belongs to only one customer and is handled by a single employee.
* **Complex Payment & Calculations:** 
  * The order's total amount is calculated dynamically by multiplying the food unit price and the order item quantity.
  * Payment amounts automatically apply customer discount rates depending on their active membership level.
* **Hierarchical Employees:** Employees are structured hierarchically, where contract/part-time workers are overseen by a specific manager. 
* **Strict Membership Limits:** A customer can have multiple historical membership records, but **only one active membership level** at any given moment. An existing membership must be terminated (by setting `endDate`) before a new one can be activated.
---

## 🗃️ Schema Architecture & Data Dictionary

The database consists of 13 strongly typed, normalized relations:

| Table Category | Tables | Description |
| :--- | :--- | :--- |
| **User & Core** | `PERSON` | Central supertype containing shared demographic and contact details. |
| **Actor Entities** | `CUSTOMER`, `EMPLOYEE` | Subtypes of `PERSON`. |
| **Employee Subtypes** | `MANAGER`, `CONTRACT_EMPLOYEE`, `PARTTIME_EMPLOYEE` | Enforces distinct payroll and scheduling attributes. |
| **Customer Subtypes** | `GUEST`, `MEMBER` | Manages visits for guests and signup periods for members. |
| **Sales & Inventory**| `ORDER_S`, `ORDER_ITEM`, `FOODITEM`, `FOOD_CATEGORY` | Core transactional system for menu selections and orders. |
| **Payments & Perks** | `PAYMENT`, `MEMBERSHIP_LEVEL` | Holds loyalty tier discounts (e.g., Platinum at 20%) and transactional records. |
---

## 🚀 Advanced PL/SQL Programming

To automate backend business logic and extract operational intelligence, the repository includes **8 custom database programs** (2 Queries, 2 Stored Procedures, and 2 Functions implemented per member):

### 🔍 1. Analytical Database Queries
Complex, multi-table queries utilizing aggregate functions, joins, and conditional grouping to evaluate:
* Sales revenue breakdowns across different food categories.
* High-value member ordering behavior and peak order timelines.

### 🛠️ 2. Stored Procedures
Automated routine scripts designed to securely maintain transactional state, including:
* Inserting new customer orders while automatically verifying item stock quantities.
* Updating active payroll attributes and managing manager-to-employee operational reporting structures.

### 📊 3. User-Defined Functions (UDFs)
Deterministic PL/SQL functions built to process variables and return real-time calculations:
* Fetching and applying precise membership discount rates matching a customer's active date window.
* Computing dynamic order sub-totals and invoicing taxation metrics.

---

## 👥 Group Members & Contributions

This project was successfully designed and built by **Wong Sin Yew (Group Leader), Chang Joo Yee, Ng Xue En, Wong Xin Tong**
