# JobSearch Design Document

## Instructions

*Save a copy of this template for your team in the same folder that contains
this template.*

*Replace italicized text (including this text!) with details of the design you
are proposing for your team project. (Your replacement text shouldn't be in
italics)*

*You should take a look at the example design document in the same folder as
this template for more guidance on the types of information to capture, and the
level of detail to aim for.*

## *Job Hunt* Design

## 1. Problem Statement

People have difficult time staying organized during job hunting.
Keeping track of which companies you have applied, the status of your applications,
which intern/apprenticeship positions are currently open, etc. 
This application is aimed to help people stay organized in their job searching
by providing a central repository for logging the job search progress. 



## 2. Top Questions to Resolve in Review

*List the most important questions you have about your design, or things that
you are still debating internally that you might like help working through.*

1.   How the frontend should interact with the API endpoints.
2.   
3.   

## 3. Use Cases

*This is where we work backwards from the customer and define what our customers
would like to do (and why). You may also include use cases for yourselves, or
for the organization providing the product to customers.*

U1. As a JobSearch customer, I want to create new Job applications and set its status/make notes. 

U2. As a JobSearch customer, I want to update my existing Job application items when the status changes.
    
U3. As a JobSearch customer, I want to delete my Job applications.

## 4. Project Scope

### 4.1. In Scope

For this MVP, CRUD operations on the Job Application will be in scope for sure.

### 4.2. Out of Scope

Web scraping and getting the recommended jobs from various job sites, displaying them
in another page for the customer.

# 5. Proposed Architecture Overview

| Aspect                      | Description                                                                                                    |
|-----------------------------|----------------------------------------------------------------------------------------------------------------|
| **Modular Backend**         | Using Lambda functions and DynamoDB, you can add new functions (like scraping and filtering) without affecting the existing structure. |
| **Scalable Data Storage**   | DynamoDB can handle additional tables or entries for new data, allowing separation between user applications and scraped job listings. |
| **API Gateway**             | API Gateway lets you easily add new endpoints (e.g., `/job-listings`), allowing seamless integration with your frontend. |
| **Frontend Flexibility**    | You can add new pages or sections to display the scraped job listings, and personalize results using JavaScript/HTML or a framework. |
| **Scheduled Jobs**          | AWS Lambda supports scheduled triggers via Amazon EventBridge, so you can run scraping functions periodically to keep listings updated. |
| **ML and Personalization**  | You can integrate AWS services like Amazon Comprehend or Amazon Personalize to analyze job listings and suggest relevant ones to users. |


# 6. API

- **Endpoint**: `POST /applications`
- **Description**: Adds a new job application for the user.
- **Request Body**:
  ```json
  {
    "userId": "user123",
    "companyName": "TechCorp",
    "jobTitle": "Software Engineer",
    "dateApplied": "2023-11-12",
    "notes": "Follow-up next week",
    "status": "Applied"
  }



# 7. Tables

# Job Application Table Schema

| Attribute      | Type     | Description                                                                                   |
|----------------|----------|-----------------------------------------------------------------------------------------------|
| `UserId`       | String   | Unique identifier for each user. Acts as the partition key.                                   |
| `ApplicationId`| String   | Unique identifier for each job application. Acts as the sort key.                             |
| `CompanyName`  | String   | Name of the company where the user applied.                                                   |
| `JobTitle`     | String   | Job title the user applied for.                                                               |
| `DateApplied`  | String   | Date the application was submitted, stored in ISO format (`YYYY-MM-DD`) for easy sorting.     |
| `Notes`        | String   | Additional notes about the application (e.g., follow-up notes, interview feedback).           |
| `Status`       | String   | Current status of the application (e.g., "Applied", "Interviewing", "Offer", "Rejected").     |

## Primary Key Design
- **Partition Key**: `UserId` - Identifies the user.
- **Sort Key**: `ApplicationId` - Uniquely identifies each job application for a specific user.


# 8. Pages

# JobSearch App

### 📋 Job Applications

#### New Application Form
- **Company Name**: [Input Field]
- **Job Title**: [Input Field]
- **Date Applied**: [Date Picker]
- **Notes**: [Textarea for notes on application status, interview feedback, etc.]
- **[Submit Button]**

---

#### Your Applications
A table or list displaying your current job applications, with options to edit or delete entries.

| Company Name   | Job Title           | Date Applied | Status          | Actions          |
|----------------|----------------------|--------------|-----------------|------------------|
| TechCorp       | Software Engineer    | 2023-11-12   | Interviewing    | [Edit] [Delete]  |
| Innovate Inc.  | Data Analyst         | 2023-10-05   | Applied         | [Edit] [Delete]  |

---
