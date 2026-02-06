# ConnectionHub

A full-featured social media platform built with Django that enables users to connect, share posts, communicate in real-time, and build their social network.

## Overview

ConnectionHub is a comprehensive social networking application that provides users with a complete social media experience. The platform includes user authentication, profile management, post creation and interaction, real-time messaging, notifications, content moderation, and a full-featured admin panel for platform management.

## Features

### User Management
- User registration and authentication with email verification
- Password recovery with OTP-based verification
- Customizable user profiles with bio, profile pictures, and personal information
- Follow/unfollow system with follower and following counts
- Private account support with follow request approval
- User blocking functionality
- User search and discovery with intelligent suggestions
- Account deletion capability

### Posts & Content
- Create, edit, and delete posts
- Image and media upload support
- Post interactions (likes, comments)
- Comment system with nested replies
- Post visibility controls
- Content reporting system
- User feed with posts from followed users

### Real-Time Communication
- WebSocket-based real-time chat system
- One-on-one messaging
- Message read status tracking
- Chat history and conversation management
- Real-time message delivery notifications

### Notifications
- Real-time notification system
- Notifications for follows, likes, comments, and messages
- Notification read/unread status
- Notification center for viewing all activities

### Content Moderation & Reporting
- User reporting system
- Post reporting functionality
- Admin review and moderation tools
- Content takedown capabilities

### Admin Panel
- Comprehensive admin dashboard
- User management (view, ban, unban users)
- Post moderation and management
- Report review and resolution
- Help center message management
- Platform analytics and statistics
- Admin authentication system

### Help Center
- User support system
- Help request submission
- Admin response management

## Technology Stack

### Backend
- **Framework**: Django 4.1.7
- **Language**: Python 3.x
- **Database**: PostgreSQL
- **Real-time**: Django Channels with WebSocket support
- **ASGI Server**: Channels with in-memory channel layer

### Security & Authentication
- Django's built-in authentication system
- Custom user model with extended fields
- Cryptography (Fernet) for data encryption
- CSRF protection
- Password validation and hashing

### Email
- SMTP email backend for notifications and verification
- OTP-based email verification
- Password reset functionality

### Media Handling
- Django's file upload system
- Image processing for profile pictures
- Static and media file management

### Environment Management
- django-environ for environment variable management
- Secure configuration with .env files

## Project Structure

```
ConnectionHub/
├── Admin/                      # Admin panel modules
│   ├── AdminHome/             # Admin dashboard and authentication
│   ├── AdminHelp/             # Help center management
│   ├── AdminPost/             # Post moderation
│   ├── AdminReports/          # Report management
│   └── AdminUsers/            # User management
├── Auth/                      # User authentication
│   ├── templates/             # Login, register, password reset
│   ├── models.py
│   ├── views.py
│   └── urls.py
├── Users/                     # User profiles and relationships
│   ├── models.py              # User, Follow, Blocks, FollowRequest
│   ├── views.py
│   └── urls.py
├── Posts/                     # Post creation and management
│   ├── models.py
│   ├── views.py
│   └── urls.py
├── Comments/                  # Comment system
│   ├── models.py
│   ├── signals.py
│   ├── views.py
│   └── urls.py
├── Communications/            # Real-time chat system
│   ├── consumer.py            # WebSocket consumer
│   ├── routing.py             # WebSocket routing
│   ├── models.py
│   └── views.py
├── Notifications/             # Notification system
│   ├── models.py
│   ├── views.py
│   └── urls.py
├── Reports/                   # Content reporting
│   ├── models.py
│   └── views.py
├── Help/                      # Help center
│   ├── models.py
│   └── views.py
├── Home/                      # Home page and settings
│   ├── views.py
│   └── urls.py
├── UsersSettings/             # User settings management
│   ├── models.py
│   └── views.py
├── ConnectionHub/             # Project configuration
│   ├── settings.py            # Django settings
│   ├── urls.py                # URL routing
│   ├── asgi.py                # ASGI configuration
│   └── wsgi.py                # WSGI configuration
├── static/                    # Static files (CSS, JS, images)
├── media/                     # User-uploaded media
├── templates/                 # Global templates
└── manage.py                  # Django management script
```

## Installation

### Prerequisites
- Python 3.8 or higher
- PostgreSQL database
- pip (Python package manager)

### Setup Steps

1. Clone the repository
```bash
git clone <repository-url>
cd ConnectionHub
```

2. Create and activate a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the project root with the following variables:
```env
SECRET_KEY=your-secret-key
DATABASE_NAME=your-database-name
DATABASE_USERNAME=your-database-username
DATABASE_PASSWORD=your-database-password
DATABASE_HOST=localhost
DATABASE_PORT=5432
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_ADDRESS=your-email@example.com
EMAIL_PASSWORD=your-email-password
DEFAULT_FROM_EMAIL=your-email@example.com
FERNET_KEY=your-fernet-key
```

5. Run database migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

6. Create a superuser
```bash
python manage.py createsuperuser
```

7. Collect static files
```bash
python manage.py collectstatic
```

8. Run the development server
```bash
python manage.py runserver
```

The application will be available at `http://localhost:8000`

## Configuration

### Database
The project uses PostgreSQL as the database backend. Configure your database credentials in the `.env` file.

### Email
Configure SMTP settings in the `.env` file for email functionality (verification, password reset, notifications).

### Media Files
User-uploaded files are stored in the `media/` directory. Ensure proper permissions are set for file uploads.

### Static Files
Static files are collected in the `staticfiles/` directory during deployment.

## Usage

### For Users
1. Register a new account with email verification
2. Complete your profile with bio and profile picture
3. Discover and follow other users
4. Create and share posts
5. Interact with posts through likes and comments
6. Send messages to other users in real-time
7. Receive notifications for activities
8. Report inappropriate content
9. Manage account settings and privacy

### For Administrators
1. Access the admin panel at `/admin/`
2. Monitor user activities and platform statistics
3. Review and moderate reported content
4. Manage user accounts (ban/unban)
5. Respond to help center requests
6. Oversee post and comment moderation

## Key Features Implementation

### Real-Time Chat
The platform uses Django Channels with WebSocket protocol for real-time bidirectional communication, enabling instant message delivery and online status updates.

### Follow System
Users can follow each other to build their social network. Private accounts require follow request approval before granting access to content.

### Content Moderation
A comprehensive reporting system allows users to flag inappropriate content, which admins can review and take action on through the admin panel.

### Notification System
Users receive real-time notifications for various activities including new followers, post interactions, messages, and follow requests.

## Security Features

- Password hashing with Django's built-in authentication
- CSRF protection on all forms
- Email verification for new accounts
- OTP-based password recovery
- Data encryption using Fernet
- User blocking and content reporting
- Admin-only access to moderation tools
- Secure session management

## License

This project is available for educational and personal use.
