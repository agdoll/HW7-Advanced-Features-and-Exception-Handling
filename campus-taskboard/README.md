# DATABASE (Spring Data JPA + H2)

### 📝 PROJECT DESCRIPTION:
This project is a Spring Boot REST API for managing tasks.
It uses Spring Data JPA with an H2 in-memory database to store data.
The API supports creating, reading, updating, deleting, searching, filtering, 
and paginating tasks. It also includes advanced features such as exception 
handling, DTOs, soft delete, request logging, and health monitoring.

### ⚙️ DATABASE CONFIGURATION:
- Database: H2 In-Memory
- URL: jdbc:h2:mem:taskboarddb
- Console: http://localhost:8080/h2-console
- Username: sa
- Password: (empty)

### ⭕ FEATURES:
- CRUD operations for tasks
- Input validation using Spring Validation
- Global exception handling with custom exceptions
- Custom error responses (ErrorResponse DTO)
- DTOs (TaskRequest, TaskResponse) for clean API structure
- Soft delete (tasks are marked as deleted instead of removed)
- Restore deleted tasks
- Request logging (logs method, URL, status, duration)
- Search and filtering (by keyword, priority, completion)
- Pagination and sorting
- Actuator health monitoring

### 📋 EACH TASK CONTAINS:
- id (unique identifier)
- title (task title)
- description (task description)
- completed (true or false)
- priority (LOW, MEDIUM, HIGH)
- createdAt (timestamp)
- updatedAt (timestamp)
- deleted (soft delete flag)

***
## SETUP AND RUN INSTRUCTIONS

### ✅ Requirements 
- Java 17 or higher 
- Intellij IDEA, VS Code or any IDE of preference 

### ▶️ Steps to Run
1. Open the project in your IDE 
2. Make sure Java 17+ is installed
3. Run the main class *CampusTaskBoardApplication.java*
4. Application runs on: http://localhost:8080

#### ➡️ Useful links
- H2 Console: http://localhost:8080/h2-console
- Actuator Health: http://localhost:8080/actuator/health


***
## 💻 API ENDPOINTS

## Base URL: 
- http://localhost:8080/api/tasks

## 1. GET All Tasks
- Method: **GET** --> /api/tasks
- Retrieves all tasks
- Returns a list of tasks in JSON format
- Status: `200 OK`

## 2. POST Create Task
- Method **POST** --> /api/tasks
- Creates a new task
- Requires JSON body with title, description, completed, and priority
- Returns the created task with an assigned ID
- Uses TaskRequest DTO 
- Returns TaskResponse DTO 
- Status: `201 Created`


   >  Example request: 

```json
{
  "title": "Complete Homework 5",
  "description": "Finish Spring Boot API assignment",
  "completed": false,
  "priority": "HIGH"
}
```
## 3. GET Task By ID
- Method: **GET**  -->  /api/tasks/{id number}
- Retrieves a specific task by its ID
- Returns the task if found
- Status: `200 OK`
- If not found: `404 Not Found`

## 4. PUT Update a Task 
- Method: **PUT** -->  /api/tasks/{id number}
- Updates an existing task by ID
- Requires JSON body with updated data
- Returns the updated task
- Status: `200 OK`
- If task not found: `404 Not Found`

## 5. DELETE a Task (Soft Delete)
- Method: **DELETE** --> /api/tasks/{id number}
- Deletes a task by its ID (does NOT remove from DB)
- No response body is returned
- Status: `204 No Content`
- If task not found: `404 Not Found`

## 6. GET research
- Method: **GET** --> /api/tasks/search?keyword={word to search}
- Searches tasks matching by title or description
- Example: /api/tasks/search?keyword=homework
- Returns matching tasks
- Status: `200 OK`

## 7. GET paginated
- Method: **GET** --> /api/tasks/paginated?page=0&size=5&sortBy=title
- Retrieves tasks with pagination and sorting
- Parameters: page (page number), size (tasks per page), sortBy (field name)
- Returns paginated tasks with metadata (total pages, total elements, etc.)
- Status: `200 OK`

## 8. GET complete
- Method: **GET** --> /api/tasks/completed
- Retrieves all completed tasks where "completed = true"
- Returns a list of completed tasks
- Status: `200 OK`

## 9. GET incomplete
- Method: **GET** --> /api/tasks/incomplete
- Retrieves all incomplete tasks
- Returns a list of incomplete tasks where "completed = false"
- Status: `200 OK`

## 10. GET filter by priority
- Method: **GET** --> /api/tasks/priority/{priority}
- Retrieves tasks filtered by priority (LOW, MEDIUM, HIGH)
- Example: /api/tasks/priority/HIGH
- Returns a list of tasks with the selected priority
- Status: 200 OK
- If invalid priority: `400 Bad Request`

## 11. PUT restore
- Method: **PUT** --> /api/tasks/{id}/restore
- Restores a soft-deleted task
- Status: `200 OK`

***

## ❌ ERROR HANDLING
The API uses **global exception handling** to ensure consistent and structured error responses.

### Each error response includes:
- Timestamp
- Status code
- Error type
- Message
- Request path

---

### 📌 HTTP Status Codes

#### `400 Bad Request`
Occurs when the request data is invalid or missing required information.

#### `404 Not Found`
Occurs when the requested task does not exist.

#### `500 Internal Server Error`
Occurs when an unexpected server error happens.


 ***

## 🍃 ACTUATOR (HEALTH MONITORING)

### Endpoints:
> - /actuator/health → shows application status
> - /actuator/info → app information
> - /actuator/metrics → system metrics

***

## ➕ REQUEST LOGGING

- Every request is logged in the console:

```text
GET /api/tasks - Status: 200 - Duration: 15ms
```

***

# ✉️ DELIVERABLES NOTE 

## 📷 SCREENSHOTS
- All screenshots are inside the folder "Screenshots"

## 📁 POSTMAN COLLECTION FILE
- Postman collection file inside "Postman Collection File" folder

## 📹 VIDEO LINK (Google Drive)
- https://drive.google.com/drive/folders/1AhaLSQcfA6CsoqNbU6hFd_mKRaTPu53x?usp=drive_link