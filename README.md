# Laravel Vue Full Stack Application

[![Laravel](https://img.shields.io/badge/Laravel-11.x-red.svg)](https://laravel.com)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-green.svg)](https://vuejs.org)
[![FrankenPHP](https://img.shields.io/badge/FrankenPHP-latest-blue.svg)](https://frankenphp.dev)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg)](https://www.mysql.com)

A modern full-stack web application featuring a Laravel RESTful API backend and Vue 3 frontend, containerized with Docker and powered by FrankenPHP. This project demonstrates a complete image management system with user authentication, file uploads, and a responsive user interface.

## 🚀 Features

- **Modern Tech Stack**: Laravel 11 API + Vue 3 frontend with Vite
- **High-Performance Backend**: FrankenPHP for modern PHP execution
- **Secure Authentication**: Laravel Sanctum token-based auth
- **Image Management**: Upload, view, delete images with validation
- **Responsive Frontend**: Mobile-first design with Tailwind CSS
- **Docker Ready**: Complete containerization with Docker Compose
- **Database**: MySQL 8.0 with persistent storage
- **Real-time Development**: Hot reload for both frontend and backend
- **API Documentation**: Comprehensive endpoint documentation
- **State Management**: Pinia for frontend state management

## 🏗 Architecture

```
┌─────────────────┐    HTTP/REST    ┌─────────────────┐
│   Vue 3 Frontend │◄──────────────►│ Laravel API     │
│   (Port 5174)    │                │ (Port 8000)     │
│                 │                │                 │
│ - Image Upload  │                │ - Auth Endpoints│
│ - Gallery View  │                │ - Image CRUD    │
│ - User Auth     │                │ - File Storage  │
└─────────────────┘                └─────────────────┘
         │                                 │
         └─────────────┬───────────────────┘
                       │
                ┌─────────────────┐
                │   MySQL 8.0     │
                │   (Port 3307)   │
                │                 │
                │ - User Data     │
                │ - Image Metadata│
                └─────────────────┘
```

## 🛠 Tech Stack

### Backend (API)
- **Framework**: Laravel 11.x
- **PHP**: 8.2+
- **Server**: FrankenPHP (Caddy-based)
- **Database**: MySQL 8.0
- **Authentication**: Laravel Sanctum
- **File Storage**: Laravel Storage (Local/Public)

### Frontend
- **Framework**: Vue 3.x (Composition API)
- **Build Tool**: Vite 6.x
- **Styling**: Tailwind CSS 3.x
- **State Management**: Pinia 2.x
- **Routing**: Vue Router 4.x
- **HTTP Client**: Axios 1.x
- **Icons**: Heroicons + Headless UI

### Infrastructure
- **Containerization**: Docker & Docker Compose
- **Web Server**: FrankenPHP
- **Database**: MySQL 8.0
- **Development**: Hot reload enabled

## 📋 Prerequisites

- Docker and Docker Compose
- Git
- (Optional) Node.js 18+ and PHP 8.2+ for local development

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/sisovin/laravel-vue.git
cd laravel-vue
```

### 2. Start the Application
```bash
docker-compose up --build
```

### 3. Run Database Migrations
```bash
docker-compose exec api php artisan migrate
```

### 4. Create a Test User (Optional)
```bash
docker-compose exec api php artisan tinker
```
```php
\App\Models\User::create([
    'name' => 'Admin',
    'email' => 'admin@example.com',
    'password' => bcrypt('SimplePass123')
]);
```

### 5. Access the Application
- **Frontend**: http://localhost:5174
- **API**: http://localhost:8000
- **API Documentation**: See [api/README.md](api/README.md)

## 📚 Detailed Documentation

### API Backend
For comprehensive API documentation, including all endpoints, authentication, and usage examples, see:
- **[API Documentation](api/README.md)** - Complete RESTful API reference

### Vue Frontend
For frontend setup, features, and development guide, see:
- **[Frontend Documentation](frontend/README.md)** - Vue 3 application guide

### Docker Setup
For detailed Docker configuration and deployment, see:
- **[Docker Setup](README-Docker.md)** - Containerization and orchestration guide

## 🎯 Application Features

### User Authentication
- **Registration**: Create new user accounts
- **Login/Logout**: Secure session management
- **Email Verification**: Account verification system
- **Password Reset**: Secure password recovery
- **Protected Routes**: Authenticated-only access

### Image Management
- **Upload Images**: Drag-and-drop or file selection
- **File Validation**: JPEG, PNG, JPG formats supported
- **Image Gallery**: Grid view of all user images
- **Delete Images**: Remove images with confirmation
- **URL Sharing**: Copy image URLs for sharing
- **Responsive Display**: Optimized for all screen sizes

### API Endpoints
- `POST /api/register` - User registration
- `POST /api/login` - User authentication
- `POST /api/logout` - Session termination
- `GET /api/user` - Current user information
- `GET /api/image` - List user images
- `POST /api/image` - Upload new image
- `DELETE /api/image/{id}` - Delete specific image

## 🔧 Development

### Local Development Setup

#### Backend (Laravel API)
```bash
cd api
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```

#### Frontend (Vue 3)
```bash
cd frontend
npm install
cp .env.example .env
npm run dev
```

### Docker Development

```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Execute commands in containers
docker-compose exec api php artisan tinker
docker-compose exec frontend sh

# Stop services
docker-compose down
```

### Testing

```bash
# API Tests
docker-compose exec api php artisan test

# Frontend (when implemented)
cd frontend && npm run test
```

### Code Quality

```bash
# PHP Code Quality
docker-compose exec api ./vendor/bin/pint
docker-compose exec api ./vendor/bin/phpstan analyse

# Frontend (when configured)
cd frontend && npm run lint
```

## 📁 Project Structure

```
laravel-vue/
├── api/                          # Laravel API Backend
│   ├── app/
│   │   ├── Http/Controllers/     # API Controllers
│   │   ├── Models/              # Eloquent Models
│   │   └── Providers/
│   ├── database/
│   │   ├── migrations/          # Database Migrations
│   │   └── seeders/             # Database Seeders
│   ├── routes/
│   │   ├── api.php              # API Routes
│   │   └── auth.php             # Auth Routes
│   ├── storage/                 # File Storage
│   ├── tests/                   # PHPUnit Tests
│   ├── Dockerfile               # API Container Config
│   └── README.md                # API Documentation
├── frontend/                     # Vue 3 Frontend
│   ├── src/
│   │   ├── components/          # Vue Components
│   │   ├── pages/               # Page Components
│   │   ├── store/               # Pinia Stores
│   │   ├── router.js            # Vue Router Config
│   │   └── axios.js             # HTTP Client Config
│   ├── public/                  # Static Assets
│   ├── Dockerfile               # Frontend Container Config
│   └── README.md                # Frontend Documentation
├── docker-compose.yml           # Docker Services
├── README-Docker.md             # Docker Setup Guide
└── README.md                    # This file
```

## 🚀 Deployment

### Production Build

```bash
# Build frontend for production
cd frontend && npm run build

# Build Docker images
docker-compose build

# Deploy with production settings
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

### Environment Configuration

Create `.env` files in respective directories:

**API (.env)**:
```env
APP_NAME=Laravel
APP_ENV=production
APP_KEY=base64:your-app-key
APP_DEBUG=false
APP_URL=http://localhost:8000

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laraveldb
DB_USERNAME=laravel
DB_PASSWORD=laravel

FRONTEND_URL=http://localhost:5174
```

**Frontend (.env)**:
```env
VITE_API_BASE_URL=http://localhost:8000
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow PSR-12 for PHP code
- Use Vue 3 Composition API
- Write tests for new features
- Update documentation as needed
- Ensure Docker compatibility

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Related Links

- [Laravel Documentation](https://laravel.com/docs)
- [Vue.js Guide](https://vuejs.org/guide)
- [FrankenPHP](https://frankenphp.dev)
- [Docker Compose](https://docs.docker.com/compose)
- [Laravel Sanctum](https://laravel.com/docs/sanctum)
- [Tailwind CSS](https://tailwindcss.com)

## 📞 Support

If you encounter any issues:

1. Check the [API Documentation](api/README.md)
2. Review the [Frontend Guide](frontend/README.md)
3. Check the [Docker Setup](README-Docker.md)
4. Search existing GitHub issues
5. Create a new issue with detailed information

## 🎉 Acknowledgments

- [Laravel](https://laravel.com) - The PHP framework
- [Vue.js](https://vuejs.org) - Progressive JavaScript framework
- [FrankenPHP](https://frankenphp.dev) - Modern PHP server
- [Docker](https://www.docker.com) - Containerization platform
- [Tailwind CSS](https://tailwindcss.com) - Utility-first CSS framework

---

**Happy coding! 🚀**
