# JMeter API Test Plan

This repository contains a JMeter test plan designed for testing a RESTful user management API.

## 📋 Test Plan Overview

- **GET /usuarios**: Fetches all users.
- **JSON Extractor**: Extracts user IDs, names, and passwords.
- **BeanShell Processor**: Saves extracted data to a CSV file.
- **DELETE /usuarios/{id}**: Deletes users using data from the CSV file (disabled by default).
- **POST /usuarios**: Creates new users (disabled by default).

## 🧪 How to Use

1. Open the `.jmx` file using Apache JMeter.
2. Run the **GET ALL USERS AND SET TO CSV** thread group.
3. (Optional) Enable and run **DELETE USERS** or **CREATE USERS** groups.
4. Review results in the **View Results Tree** listener.

## 📂 Folder Structure

- `test-plan/`: Contains the `.jmx` file.
- `data/`: (Optional) Stores the generated `user_ids.csv`.

## ⚙️ Requirements

- Apache JMeter 5.6.3 or compatible.

## 📄 License

MIT License
