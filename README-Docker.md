# Laravel Vue Full Stack on FrankenPHP + Docker

This setup runs the Laravel API using FrankenPHP and the Vue.js frontend using Node.js in Docker containers.

## Prerequisites

- Docker and Docker Compose installed

## Setup

1. **Build and start the containers:**
   ```bash
   docker-compose up --build
   ```

2. **Run database migrations:**
   ```bash
   docker-compose exec api php artisan migrate
   ```

3. **Create a test user (optional):**
   ```bash
   docker-compose exec api php artisan tinker
   ```
   Then in tinker:
   ```php
   \App\Models\User::create(['name' => 'Admin', 'email' => 'admin@example.com', 'password' => bcrypt('SimplePass123')]);
   ```

4. **Access the application:**
   - Frontend: http://localhost:5174
   - API: http://localhost:8000

## Services

- **api**: Laravel application running on FrankenPHP
- **db**: MySQL 8.0 database
- **frontend**: Vue.js development server

## Notes

- The API uses FrankenPHP for modern PHP execution
- Database data persists in a Docker volume
- Frontend hot-reload is enabled for development