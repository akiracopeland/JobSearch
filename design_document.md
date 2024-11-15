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

Dynamo DB Table JobApplication that holds all the Job Application items.
AWS Lambda functions that handle API calls.
API Gateway to expose the endpoints.
Frontend that calls the endpoints when CRUD operation is done.

# 6. API

## 6.1. Public Models

*Define the data models your service will expose in its responses via your
*`-Model`* package. These will be equivalent to the *`PlaylistModel`* and
*`SongModel`* from the Unit 3 project.*

## 6.2. *First Endpoint*

*Describe the behavior of the first endpoint you will build into your service
API. This should include what data it requires, what data it returns, and how it
will handle any known failure cases. You should also include a sequence diagram
showing how a user interaction goes from user to website to service to database,
and back. This first endpoint can serve as a template for subsequent endpoints.
(If there is a significant difference on a subsequent endpoint, review that with
your team before building it!)*

*(You should have a separate section for each of the endpoints you are expecting
to build...)*

## 6.3 *Second Endpoint*

*(repeat, but you can use shorthand here, indicating what is different, likely
primarily the data in/out and error conditions. If the sequence diagram is
nearly identical, you can say in a few words how it is the same/different from
the first endpoint)*

# 7. Tables

*Define the DynamoDB tables you will need for the data your service will use. It
may be helpful to first think of what objects your service will need, then
translate that to a table structure, like with the *`Playlist` POJO* versus the
`playlists` table in the Unit 3 project.*

# 8. Pages

*Include mock-ups of the web pages you expect to build. These can be as
sophisticated as mockups/wireframes using drawing software, or as simple as
hand-drawn pictures that represent the key customer-facing components of the
pages. It should be clear what the interactions will be on the page, especially
where customers enter and submit data. You may want to accompany the mockups
with some description of behaviors of the page (e.g. “When customer submits the
submit-dog-photo button, the customer is sent to the doggie detail page”)*
