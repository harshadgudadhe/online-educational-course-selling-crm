# Online Educational Course Selling CRM

> ⚠️ **Status: Work in Progress.** Customer and Employee panels are fully functional. A few specific features in the Admin panel and the course purchase flow are currently broken — see [Known Issues](#known-issues) below.

A 3-role (Admin, Employee, Customer) CRM web application for selling online programming courses. Built with Spring Boot, Hibernate, and MySQL, modeling a real sales pipeline — Inquiry → Follow-up → Order — alongside course catalog management and customer purchases.

## Tech Stack
- **Backend:** Java 17, Spring Boot, Spring Data JPA, Hibernate ORM
- **Database:** MySQL
- **Frontend:** Thymeleaf, HTML5, CSS3, JavaScript
- **Build tool:** Maven
- **API:** Mixed — Thymeleaf server-rendered views for dashboards, plus REST endpoints (`FollowUpsApi`, `InquiryApi`, `OrdersApi`)

## Roles & Features

Status legend: ✅ Working &nbsp; ⚠️ Partially working &nbsp; ❌ Not working / in progress

### Admin (`/adminLogin`)
- ✅ Dashboard with sales analytics (today's sales, courses sold, daily sales trend)
- ⚠️ Course management — list, edit, delete work; **adding a new course currently fails**
- ✅ Employee management (add, update, delete)
- ✅ Sales overview by employee
- ❌ Customer management — not functional yet
- ❌ Feedback view — not functional yet

### Employee (`/employeeLogin`)
- ✅ Profile management
- ✅ Course selling
- ✅ Inquiry management (incoming customer leads)
- ✅ Follow-up tracking on inquiries

### Customer (Login via home page)
- ✅ Registration and login
- ✅ Browse available courses
- ❌ Purchase courses — currently broken, likely a payment gateway integration issue
- ✅ View purchased courses
- ✅ Submit feedback

## Test Credentials
| Role | Email | Password |
|------|-------|----------|
| Admin | admin@gmail.com | admin123 |
| Employee | employee@gmail.com | employee123 |
| Customer | customer@gmail.com | customer123 |

*(These are local development/demo credentials only — not connected to any live or production system.)*

## Known Issues
Customer and Employee panels are fully functional end-to-end. The remaining known issues are scoped to the Admin panel and the payment step of the purchase flow:

- **Add Course** (Admin panel) — course creation currently fails; under investigation, likely related to image upload path handling
- **Customer Management** (Admin panel) — not yet functional
- **Feedback view** (Admin panel) — not yet functional
- **Course purchase** (Customer panel) — currently broken, likely due to a payment gateway integration issue; fix in progress

These are being worked through incrementally and are tracked actively.

## Setup & Running Locally

1. Clone the repository:
   ```
   git clone https://github.com/harshadgudadhe/online-educational-course-selling-crm.git
   ```

2. Create a MySQL database:
   ```sql
   CREATE DATABASE education_crm_db;
   ```

3. Copy `src/main/resources/application.properties.example` to `src/main/resources/application.properties` and fill in your own MySQL credentials:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/education_crm_db
   spring.datasource.username=your_mysql_username
   spring.datasource.password=your_mysql_password
   ```

4. Run the application:
   ```
   mvnw spring-boot:run
   ```

5. Open `http://localhost:8080` in your browser.

## Project Background
This project was originally built while learning Spring Boot, Hibernate, and REST API development during an MCA program, and is now being independently extended, debugged, and improved — including fixing the issues listed above and a planned UI consistency pass across the Admin and Employee panels.