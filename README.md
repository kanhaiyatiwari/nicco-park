# Nicco Park – Amusement Park Booking API

<p align="center">
  <img src="https://user-images.githubusercontent.com/107462648/221474006-506a45e6-c1e6-4b24-b31a-aeab61433c57.jpeg" alt="Nicco Park" width="700">
</p>

<p align="center">
  <a href="https://drive.google.com/file/d/1M_MO7uC3gaH2bgrjPWcy-fzk0NPRCKLf/view"><b>Demo video</b></a> ·
  <a href="#setup--installation">Run locally</a> ·
  <a href="#api-endpoints">API endpoints</a>
</p>

## Project Description

Nicco Park is a Spring Boot REST API for running an amusement park. Admins manage activities, time slots and customers; customers sign up, book tickets for activities and manage their bookings. The goal was to give a frontend team a clean set of APIs for every booking flow, with session-based login, validation and clear error responses.

Built in 5 days by a team of 4 during the Masai School construct week.

## Tech Stack

| Area | Tools |
|---|---|
| Language | Java 17 |
| Framework | Spring Boot 3.0, Spring Web, Spring Data JPA, Bean Validation |
| Database | MySQL, Hibernate (ORM) |
| API docs | springdoc-openapi (Swagger UI) |
| Build & tools | Maven (multi-module), Lombok, Spring Boot DevTools, Postman |

## Key Features

**Admin**
- Sign up, log in and log out (session key based)
- Add activities and time slots, and link slots to activities
- Update or remove activities and customers
- Reports: activities by customer, by date and by date range, and total revenue

**Customer**
- Sign up, log in and log out; update profile, username and password
- Book a ticket for an activity and slot, and see the bill
- Change a ticket's activity, slot or date, or cancel it

**Engineering**
- Multi-module Maven project: `Entity`, `Repository`, `Service`, `Controller`, `Exception`
- DTOs for requests and responses, Bean Validation on inputs
- Global exception handling with clear error messages
- Swagger UI for trying every endpoint

## Entity Relationship Diagram

![ER Diagram](https://user-images.githubusercontent.com/107462648/221478459-4a74ccc1-0f84-40b9-87bb-63c3b9c7f450.png)

## Setup & Installation

**Prerequisites:** Java 17, Maven 3.8+, MySQL 8

1. Clone the repository
   ```bash
   git clone https://github.com/kanhaiyatiwari/nicco-park.git
   cd nicco-park
   ```
2. Create the database
   ```sql
   CREATE DATABASE db;
   ```
3. Set your MySQL username and password in `Repository/src/main/resources/application.properties`
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/db
   spring.datasource.username=root
   spring.datasource.password=your_password
   ```
   Tables are created on startup (`spring.jpa.hibernate.ddl-auto=update`).
4. Build all modules and start the app
   ```bash
   mvn clean install
   cd Controller
   mvn spring-boot:run
   ```
5. Open Swagger UI at **http://localhost:8888/swagger-ui/index.html**

## API Endpoints

| Resource | Base path | Examples |
|---|---|---|
| Admins | `/admins` | `POST /admin_sign_up`, `POST /login_admin`, `GET /get_revenue`, `GET /get_activities_datewise` |
| Customers | `/customers` | `POST /customer_sign_up`, `POST /login_customer`, `PUT /update_customer_details` |
| Activities | `/activities` | `POST /add_activity`, `POST /add_slot`, `PUT /add_slots_to_activity/{activityId}/{slotId}` |
| Tickets | `/tickets` | `POST /book_a_ticket`, `GET /calculate_bill`, `PUT /update_tickets_slot_or_date/{ticketId}` |

The full list with request and response bodies is in Swagger UI.

## Team

- Subhadeep Bid
- Jayesh Ravindra Thakare
- Kanhaiya Lal Tiwari
- Shiv Kumar
