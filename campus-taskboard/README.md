# DATABASE (Spring Data JPA + H2)

### PROJECT DESCRIPTION 
This project is a Spring Boot REST API for managing tasks. 
It uses Spring Data JPA with an H2 in-memory database to store data and 
users can create, read, update, delete, search, filter, and paginate tasks.

### DATABASE CONFIGURATION:
- Database: H2 In-Memory
- URL: jdbc:h2:mem:taskboarddb
- Console: http://localhost:8080/h2-console
- Username: sa
- Password: (empty)

### FEATURES:
- Tasks are stored during application runtime (data is lost when the server stops because H2 is in-memory)
- Database tables are generated automatically from JPA Entity
- Hibernate handles SQL generation
- SQL queries are visible in console

### EACH TASK CONTAINS:
- id (unique identifier)
- title (task title)
- description (task description)
- completed (true or false)
- priority (LOW, MEDIUM, HIGH)
- createdAt (timestamp)
- updatedAt (timestamp)

### SETUP AND RUN INSTRUCTIONS 
 
# Requirements 
- Java 17 or higher 
- Intellij IDEA, VS Code or IDE of preference 

# Steps to Run
1. Open the project in an IDE (like IntelliJ, VS Code, or the 
IDE of your preference).
2. Make sure you have Java 17+.
3. Build and run the application:
  - Run the main class CampusTaskBoardApplication.java
4. The application will run on: http://localhost:8080
5. To view the database: http://localhost:8080/h2-console 

# API ENDPOINTS

### New Request
Base URL: "http://localhost:8080/api/tasks"

# 1- GET All Tasks
- Method: **GET** --> /api/tasks
- Retrieves all tasks
- Returns a list of tasks in JSON format
- Status: 200 OK

# 2- POST Create Task
- Method **POST** --> /api/tasks
- Creates a new task
- Requires JSON body with title, description, completed, and priority
- Returns the created task with an assigned ID
- Status: 201 Created
- Example request:
--> raw - json
{
  "title": "Complete Homework 5",
  "description": "Finish Spring Boot API assignment",
  "completed": false,
  "priority": "HIGH"
}

# 3- GET Task By ID
- Method: **GET**  -->  /api/tasks/{id number}
- Retrieves a specific task by its ID
- Returns the task if found
- Status: 200 OK
- If not found: 404 Not Found

# 4- PUT Update a Task 
- Method: **PUT** -->  /api/tasks/{id number}
- Updates an existing task by ID
- Requires JSON body with updated data
- Returns the updated task
- Status: 200 OK
- If task not found: 404 Not Found

# 5- DELETE a Task
- Method: **DELETE** --> /api/tasks/{id number}
- Deletes a task by its ID
- No response body is returned
- Status: 204 No Content
- If task not found: 404 Not Found

# VALIDATION
The API validates input data using Spring Validation:
-  Task title in blank:
   - Message: "Title is required"
-  Task title length less than 3 characters:
   - Message: "Title must be between 3 and 100 characters"
- Task description length more than 500 characters: 
  - Message: "Description cannot exceed 500 characters" 

# NEW ENDPOINTS (HOMEWORK 6)

# 6- GET research
- Method: **GET** --> /api/tasks/search?keyword={word to search}
- Searches tasks matching by title or description
- Example: /api/tasks/search?keyword=homework
- Returns matching tasks
- Status: 200 OK

# 7- GET paginated
- Method: **GET** --> /api/tasks/paginated?page=0&size=5&sortBy=title
- Retrieves tasks with pagination and sorting
- Parameters: page (page number), size (tasks per page), sortBy (field name)
- Returns paginated tasks with metadata (total pages, total elements, etc.)
- Status: 200 OK

# 8- GET completed
- Method: **GET** --> /api/tasks/completed
- Retrieves all completed tasks where "completed = true"
- Returns a list of completed tasks
- Status: 200 OK

# 9- GET incompleted
- Method: **GET** --> /api/tasks/incomplete
- Retrieves all incomplete tasks
- Returns a list of incomplete tasks where "completed = false"
- Status: 200 OK

# 10- GET filter by priority
- Method: **GET** --> /api/tasks/priority/{priority}
- Retrieves tasks filtered by priority (LOW, MEDIUM, HIGH)
- Example: /api/tasks/priority/HIGH
- Returns a list of tasks with the selected priority
- Status: 200 OK
- If invalid priority: 400 Bad Request

## SCREENSHOTS 
- All screenshots are inside the folder named "Screenshots"

# POSTMAN COLLECTION FILE
- Postman collection file inside "Postman Collection File" folder

# VIDEO LINK (Drive)
- https://drive.google.com/drive/folders/13zWH8TEOgbV--apizki_UybYY-Nh4B_l?usp=drive_link

