# Task Management API

A RESTful API built with Lumen for managing tasks. The API provides CRUD operations for tasks with features like filtering, pagination, and search functionality.

## Features

- Full CRUD operations for tasks
- Input validation
- PostgreSQL database integration
- Task filtering by status and due date
- Pagination support
- Search functionality by task title

## Requirements

- PHP >= 7.4
- PostgreSQL
- Composer

## Installation

1. Clone the repository
```bash
git clone [your-repository-url]
cd task-management-api
```

2. Install dependencies
```bash
composer install
```

3. Set up environment variables
```bash
cp .env.example .env
```
Update the following variables in `.env`:
```
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=your_database_name
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

4. Run migrations
```bash
php artisan migrate
```

5. Start the development server
```bash
php -S localhost:8000 -t public
```

## API Endpoints

### Get All Tasks
```
GET /api/tasks
```
Query Parameters:
- `status`: Filter by status (pending/completed)
- `due_date`: Filter by due date (YYYY-MM-DD)
- `search`: Search tasks by title
- `page`: Page number for pagination

### Get Single Task
```
GET /api/tasks/{id}
```

### Create Task
```
POST /api/tasks
```
Request Body:
```json
{
    "title": "Task Title",
    "description": "Task Description",
    "due_date": "2024-12-31"
}
```

### Update Task
```
PUT /api/tasks/{id}
```
Request Body:
```json
{
    "title": "Updated Title",
    "description": "Updated Description",
    "status": "completed",
    "due_date": "2024-12-31"
}
```

### Delete Task
```
DELETE /api/tasks/{id}
```

## Validation Rules

- `title`: Required, unique
- `description`: Optional
- `status`: Optional (defaults to "pending")
- `due_date`: Required, must be a future date

## Testing

The project includes comprehensive test coverage. To run tests:

```bash
./vendor/bin/phpunit
```

## Database Schema

The tasks table includes the following fields:
- `id` (primary key)
- `title` (unique string)
- `description` (nullable text)
- `status` (string, default: "pending")
- `due_date` (date)
- `created_at` (timestamp)
- `updated_at` (timestamp)

## Implementation Notes

- Used Lumen framework for lightweight, fast API development
- Implemented proper HTTP status codes for responses
- Added validation for all incoming requests
- Included error handling with appropriate error messages
- Implemented bonus features for enhanced functionality

## Future Improvements

While the current implementation meets all requirements, potential improvements could include:
- Authentication/Authorization
- Task categories
- Priority levels
- Due date reminders
- Request rate limiting
- Response caching

## Contact

For any questions regarding this submission, please contact [Your Name] at [your.email@example.com]
