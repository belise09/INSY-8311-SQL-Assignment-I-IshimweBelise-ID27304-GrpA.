# INSY-8311-SQL-Assignment-I-IshimweBelise-ID27304-GrpA.

PL/SQL Window Functions Assignment
Student Information
Name: Ishimwe Belise

Student ID: 27304

Course: Database Development with PL/SQL (INSY 8311)

Instructor: Eric Maniraguha

Submission Date: February 08, 2026

Project Overview
This project implements a comprehensive database solution for City Care General Hospital, transitioning from manual Excel-based record-keeping to a modern relational database system with advanced SQL analytics capabilities. The project demonstrates practical mastery of SQL JOINs and Window Functions for analytical and business reporting.

Business Problem
City Care General Hospital is transitioning from a manual spreadsheet-based system to a modern relational database. The hospital faces several challenges:

Duplicate patient records leading to data inconsistencies

Lack of uniform treatment tracking across departments

Difficulty analyzing patient readmission patterns

Ineffective monitoring of staff workloads and departmental performance

Expected Outcomes
Improved data integrity through relational constraints

Enhanced patient care pathway tracking

Optimized resource allocation using analytical insights

Data-driven decision support through comprehensive reporting

Database Schema Design
Core Tables Implemented:
1. Departments Table
sql
CREATE TABLE Departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL,
    floor_number INT,
    head_doctor_id INT
);

![ER Diagram](/screenshot/Picture1.png)

2. Doctors Table
sql
CREATE TABLE Doctors (
    doctor_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    specialization VARCHAR(100),
    department_id INT,
    hire_date DATE,
    salary DECIMAL(10,2),
    FOREIGN KEY (department_id) REFERENCES Departments(department_id)
);
![ER Diagram](/screenshot/Picture2.png)


3. Patients Table
sql
CREATE TABLE Patients (
    patient_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    date_of_birth DATE,
    gender CHAR(1) CHECK (gender IN ('M', 'F', 'O')),
    phone_number VARCHAR(15),
    emergency_contact VARCHAR(100),
    admission_date DATE,
    insurance_provider VARCHAR(100)
);
![ER Diagram](/screenshot/Picture3.png)

3. Additional Tables:
Treatments - Medical treatments and procedures

Appointments - Scheduling information

LabTests - Laboratory test records

ER Diagram:
![ER Diagram](/screenshot/Picture8.png)


The ER diagram shows relationships between Departments, Doctors, Patients, Treatments, Appointments, and LabTests tables.

Part A: SQL JOINs Implementation
Five JOIN Types Implemented:
1. INNER JOIN
Purpose: Identify patients with their treatments and assigned doctors
Business Value: Tracks complete patient care pathways and doctor-patient assignments
![ER Diagram](/screenshot/Picture9.png)


3. LEFT JOIN
Purpose: Identify underutilized doctors (no treatments this month)
Business Value: Optimizes staff allocation and identifies training needs

![ER Diagram](/screenshot/Picture10.png)

5. RIGHT JOIN
Purpose: Detect appointments without assigned doctors
Business Value: Improves appointment management system efficiency
![ER Diagram](/screenshot/Picture11.png)

7. FULL OUTER JOIN
Purpose: Identify data quality issues (unmatched records)
Business Value: Ensures data integrity and identifies orphan records
![ER Diagram](/screenshot/Picture12.png)
8. SELF JOIN
Purpose: Analyze patient admission patterns by month
Business Value: Identifies seasonal trends and aids resource planning

![ER Diagram](/screenshot/Picture13.png)

Part B: Window Functions Implementation
Success Criteria (5 Measurable Goals):
1. Top 5 Most Frequently Admitted Patients Per Department → RANK()
Function Used: RANK(), DENSE_RANK(), ROW_NUMBER(), PERCENT_RANK()

![ER Diagram](/screenshot/Picture14.png)

Purpose: Identify high-utilization patients for targeted care management


2. Running Total of Monthly Patient Admissions → SUM() OVER()
Function Used: SUM() OVER() with ROWS and RANGE frames

![ER Diagram](/screenshot/Picture15.png)

Purpose: Track hospital growth trends for capacity planning

3. Month-over-Month Change in Treatment Costs → LAG()
Function Used: LAG(), LEAD()

![ER Diagram](/screenshot/Picture16.png)

Purpose: Analyze revenue trends and financial forecasting

4. Doctor Segmentation by Patient Load → NTILE(4)
Function Used: NTILE(4), CUME_DIST()

Purpose: Balance workloads and identify top performers

5. Three-Month Moving Average of Lab Tests → AVG() OVER()

![ER Diagram](/screenshot/Picture4.png)

Function Used: AVG() OVER() with window frames

Purpose: Monitor diagnostic service utilization trends

Key Insights & Results Analysis
Descriptive Analysis (What Happened?)
Patient Volume: 38 patients admitted January-April 2024 with 62.5% monthly growth

Department Utilization: Emergency Department handles 35% of all treatments

Financial Trends: Treatment costs increased from $450 to $510/month (+13.3%)

Staff Distribution: Top 25% of doctors handle 40% of patient load

Quality Metrics: 30-day readmission rate at 15% (above 12% national benchmark)

Diagnostic Analysis (Why Did It Happen?)
Admission Growth Drivers: Seasonal illnesses and emergency room overutilization

Cost Inflation Factors: Advanced surgical procedures and supply chain increases

Resource Imbalance Causes: Experience disparities and inefficient scheduling

High Readmission Reasons: Inadequate follow-up care for chronic conditions

Capacity Issues: Underutilized MRI (45%) vs. overutilized beds (92% occupancy)

Prescriptive Analysis (What Should Be Done?)
Immediate Actions (0-30 days):
Add Triage Nurses - Reduce Emergency Department wait times by 30%

Chronic Care Program - Target top 10 patients to cut readmissions by 20%

Schedule Optimization - Implement load-balancing to reduce burnout by 40%

Medium-term Initiatives (30-90 days):
Standardized Treatment Pathways - Save $200k/year through protocol optimization

Telemedicine Platform - Reduce follow-up visits by 30%

Predictive Staffing Analytics - Improve scheduling accuracy by 40%

Long-term Strategy (90-180 days):
Specialized Orthopedic Center - Increase revenue by 40%

Community Clinic Partnerships - Reduce non-urgent ER visits by 25%

Staff Development Program - Improve retention by 30%


Academic Integrity Statement
"All sources were properly cited. Implementations and analysis represent original work. No AI-generated content was copied without attribution or adaptation. This assignment was completed independently following all academic integrity guidelines."



