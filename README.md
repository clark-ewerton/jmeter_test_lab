# JMeter API Test Plan

This repository contains a JMeter test plan designed for testing a RESTful user management API.

Sample project to experiment with [Jmeter](https://jmeter.apache.org/) to test the ServeRest app in localhost using Docker Image.

[![Badge ServeRest](https://img.shields.io/badge/API-ServeRest-green)](https://github.com/ServeRest/ServeRest/)
![License](https://img.shields.io/badge/license-MIT-blue)


## 📋 Test Plan Overview

The idea is to hit /login endpoint (the steps below were designed to do so)

- **GET ALL USERS /usuarios AND set it to a CSV file**: Fetches all users and save it to a CSV file.
  - **JSR223 PostProcessor - set userId, userEmail and userPassword to csv**: Extracts user IDs, emails, and passwords.
  - **HTTP Header Manager**: Managers headers content-type
- **DELETE USER ID /usuarios/${user_id}**: The idea is to delete all users present on database before creation of it
  - **CSV DataSet Config - read user_id.csv and fetch userId**: It's gonna read the csv file created before to fetch mainly userId
  - **HTTP Header Manager**: Managers headers content-type
- **POST CREATE USER /usuarios**: Create user
  - **HTTP Header Manager**: Managers headers content-type
- **GET ALL USERS /usuarios AND set it to a CSV file**: Fetches all users again and save it to a CSV file.
  - **JSR223 PostProcessor - set userId, userEmail and userPassword to csv**: Extracts user IDs, emails, and passwords.
  - **HTTP Header Manager**: Managers headers content-type
- **POST LOGIN USERS /login AND set it to a CSV file**: Fetches all users and save it to a CSV file.
  - **CSV DataSet Config - read user_id.csv and fetch email and password's user**: Extracts user email and passwords.
  - **JSR223 PostProcessor - save on memory's variables all the bearer tokenssave on memory's variables all the bearer tokens**
  - **HTTP Header Manager**: Managers headers content-type
- **SET BEARER TOKENS TO CSV**: Export all bearer tokens to a new CSV file
  - **JSR223 Sampler - set bearer tokens to csv**: Export all bearer tokens to a new CSV file

## 🧪 How to Use

1. Open the `.jmx` file using Apache JMeter.
2. Please change the number of Threads to the following Thread Groups: DELETE USERS, CREATE USERS and LOGIN USERS
3. (Optional) Enable and run **DELETE USERS** or **CREATE USERS** groups.
4. Review results in the **View Results Tree** listener or **Aggregate Reports**. (It's gonna generate a report.csv)
5. To generate the report, please use the following command (for Windows):
 navigate into jmeter folder
cd C:\Users\clark\OneDrive\Documentos\projetos\apache-jmeter-5.6.3\apache-jmeter-5.6.3\bin
:: then generate reports
jmeter -g "C:\Users\clark\OneDrive\Documentos\projetos\apache-jmeter-5.6.3\report.csv" -o "C:\Users\clark\OneDrive\Documentos\projetos\apache-jmeter-5.6.3\report\report.html"

## 📋 Results

1. Running in localhost from a Docker Imagem considering that my Windows' machine has 8GB ram + Intel(R) Core(TM) i5-10210U CPU @ 1.60GHz   2.11 GHz + Windows 10. The results is that 1000 threads were accepted for all endpoints considering a ramp-up of 1s. More than this is practically the break's point of the system overloading CPU's usage:

![Local testing execution example](assets/mypipelineJenkins.png)
![Local testing execution example](assets/pipelineExecution.png)

## ⚙️ Requirements

- Apache JMeter 5.6.3 or compatible.

## 📄 License

MIT License
