# Laravel To-Do List API

A simple To-Do list API built with Laravel.

## Setup Instructions

Follow these steps to get the application up and running.

### Prerequisites

- MySQL Server
- Redis Server
- PHP 8.3
- PHP Composer

### Installation Steps

1. **Create MySQL and Redis servers**

   Ensure that you have MySQL and Redis servers set up and running.

2. **Copy `.env` file**

   ```bash
   cp .env.example .env
   ```

3. **Update `.env` file**

   Update the `.env` file with your environment-specific details, such as database credentials and Redis connection.

4. **Install Dependencies**

   ```bash
   composer install
   ```

5. **Generate Application Key**

   ```bash
   php artisan key:generate
   ```

6. **Run Database Seeder**

   ```bash
   php artisan db:seed
   ```

7. **Serve site with herd or valet or nginx**

    #### herd example
    ```bash
   herd domain test
   herd link laravel-todolist-api
   herd secure --site=laravel-todolist-api
   ```
   
Follow official documentation for nginx configuration and valet.

### Verify Application Functionality

You can test the application using the following HTTP requests:

#### 1. Register

**Request:**

```http
POST https://laravel-todolist-api.test/api/register
Content-Type: application/json

{
  "name": "user",
  "email": "user@user.com",
  "password": "password",
  "password_confirmation": "password"
}
```

#### 2. Login

**Request:**

```http
POST https://laravel-todolist-api.test/api/login
Content-Type: application/json

{
  "email": "user@user.com",
  "password": "password"
}
```

#### 3. Create To-Do Item

**Request:**

```http
POST https://laravel-todolist-api.test/api/todo
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json

{
  "title": "todo title",
  "description": "todo description",
  "completed": "0"
}
```

#### 4. List To-Do Items

**Request:**

```http
GET https://laravel-todolist-api.test/api/todo
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
```

#### 5. To-Do Item Detail

**Request:**

```http
GET https://laravel-todolist-api.test/api/todo/1
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json

{
  "completed": 1
}
```

#### 6. Update To-Do Item

**Request:**

```http
PATCH https://laravel-todolist-api.test/api/todo/1
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json

{
  "title": "todo title",
  "description": "todo description",
  "completed": "1"
}
```

#### 7. Delete To-Do Item

**Request:**

```http
DELETE https://laravel-todolist-api.test/api/todo/1
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
```

---

Replace `YOUR_ACCESS_TOKEN` with the actual token obtained during login for authorization.
