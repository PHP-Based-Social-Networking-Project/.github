# PHP-Based Social Networking Project Guide

A structured approach to building social networking applications using a custom PHP pattern inspired by scripts like WoWonder. The focus is on creating modular, extensible, and secure web apps without relying on heavy frameworks.

## 🚀 Introduction

This guide outlines a structured approach to building social networking applications using a custom PHP pattern inspired by scripts like WoWonder. You'll learn to organize code in a consistent file structure and apply it through three progressive projects.

The primary language is PHP (version 7.4+ or 8.x recommended). Start with PHP fundamentals (variables, functions, sessions, OOP basics) before diving in.

## 📋 Prerequisites & Technologies

### Primary Language
- **PHP 7.4+ or 8.x** (recommended)
- Basic PHP fundamentals: variables, functions, sessions, OOP basics

### Supporting Technologies
- **JavaScript** (vanilla or with jQuery) for front-end interactivity and AJAX
- **HTML/CSS** for views (use Bootstrap-inspired styles for responsiveness)
- **Node.js** with Socket.io for real-time features (e.g., chat, notifications)
- **MySQL** for the database (focus on CRUD operations and schema design)

### Other Tools
- **Composer** (optional for dependencies)
- **Cron jobs** for background tasks
- **.htaccess** for URL rewriting

## 🔒 Best Practices

- **Emphasize security**: Use prepared statements (PDO/MySQLi), hash passwords (password_hash()), sanitize inputs, and add CSRF tokens
- **Keep code modular**: Use include/require for reusability; avoid monolithic files
- **Test locally** (e.g., XAMPP) and secure uploads/media handling
- **Make projects extensible**: Use hooks (e.g., override functions) for custom features

## 🏗️ Code Structure Pattern

Organize your project directories as follows for separation of concerns (MVC-like: Models for data/logic, Views for UI, Controllers for request handling). This structure promotes scalability and easy theming/plugins.

```
my-social-project/                    # Root Directory
├── assets/                           # Static resources
│   ├── js/                          # JavaScript files (e.g., core.js for global scripts, chat.js for real-time)
│   ├── css/                         # Stylesheets (e.g., main.css for site-wide styles)
│   ├── img/                         # Default images (logos, icons)
│   └── uploads/                     # User-uploaded media (secure this folder with permissions)
├── themes/                          # Modular themes for UI customization
│   └── default/                     # (or custom theme name)
│       ├── layout/                  # PHP/HTML views (e.g., header.php, footer.php, post.php)
│       ├── javascript/              # Theme-specific JS
│       ├── stylesheet/              # Theme CSS
│       └── img/                     # Theme images
├── xhr/                             # AJAX handlers (e.g., like_post.php, send_message.php for async operations)
├── requests/                        # Controllers (e.g., login.php, profile.php for handling HTTP requests)
├── sources/                         # Models and utilities (e.g., user.php for user logic, db.php for DB connections)
│   └── classes/                     # Alternative naming for models
├── admin-panel/                     # Admin dashboard (mini-structure for security)
│   ├── pages/                       # Admin views (e.g., dashboard.php)
│   ├── actions/                     # Admin controllers (e.g., ban_user.php)
│   └── assets/                      # Admin JS/CSS
├── api/                             # RESTful API endpoints (e.g., v1/user.php for JSON responses)
├── nodejs/                          # Real-time server (e.g., server.js with Socket.io)
├── includes/                        # Third-party libraries (e.g., email or image processing classes)
├── config.php                       # Central config (DB credentials, site URL, API keys)
├── functions.php                    # Global helpers (e.g., sanitization, auth checks)
├── install.php                      # Setup script (creates DB tables, initial configs)
├── index.php                        # Main entry point (routes requests, loads config/sessions)
├── .htaccess                        # For clean URLs (e.g., rewrite rules)
├── cron.php                         # Background tasks (e.g., email queues, run via server cron)
└── database.sql                     # Database schema file
```

## 🛠️ Building Steps

1. **Configure** config.php and database
2. **Implement models** in sources/
3. **Add controllers** in requests/ (fetch data, render views)
4. **Create views** in themes/default/layout/
5. **Add JS/CSS** in assets/
6. **Secure and test**

**Database Setup**: Use MySQL. Include a database.sql file for schema (e.g., tables like users, posts). Run via install.php.

## 📚 Project Samples

Apply the structure to these projects, starting simple and building complexity. Each includes features, utilization of the pattern, and build guidance.

### Project 1: Basic Social Profile Network (Beginner Level)

Build a simple platform for user profiles, posts, and follows. **Focus**: Authentication, CRUD, basic feeds.

#### Key Features:
- Registration/login with hashing
- Profile edit/view (bio, avatar)
- Text posts with likes/comments
- Follow/unfollow and feed of followed posts
- Admin user management

#### Utilization of Structure:
- **PHP**: Procedural for controllers; OOP for models (e.g., User class)
- **Database**: Tables: users, posts, follows

#### Mapping:
- `config.php`: DB settings
- `sources/`: user.php (register/login), post.php (CRUD)
- `requests/`: register.php (form processing), profile.php (data fetch/view)
- `themes/default/layout/`: profile.php (dynamic HTML), feed.php (post loop)
- `xhr/`: like_post.php (AJAX likes)
- `assets/js/`: interactions.js (AJAX/validations)
- `admin-panel/`: pages/users.php (list), actions/ban_user.php
- `index.php`: Routing (e.g., /profile/123 → requests/profile.php)
- `.htaccess`: Clean URLs

#### Build Guidance:
- Start with auth, add posts, then feeds
- **Extensions**: Add CSS responsiveness
- **Outcomes**: Learn separation, security, modularity

### Project 2: Real-Time Chat Forum (Intermediate Level)

Create a forum with discussions and messaging. **Focus**: Real-time, APIs, async.

#### Key Features:
- User search/friend requests
- Public forums (threads/replies), private chats
- Real-time messages/notifications
- Media uploads in chats
- Admin moderation

#### Utilization of Structure:
- **PHP**: Async handling; APIs for integration
- **Supporting**: Node.js for WebSockets; JS for UI
- **Database**: Tables: messages, forums, forum_replies

#### Mapping:
- `config.php`: Socket.io settings
- `sources/`: chat.php (send/get), forum.php (threads)
- `requests/`: forum.php (display), message.php (send)
- `themes/default/layout/`: chat_window.php, forum_thread.php
- `xhr/`: fetch_messages.php (JSON)
- `api/`: v1/send_message.php
- `assets/js/`: chat.js (WebSockets)
- `nodejs/`: server.js (broadcasting)
- `admin-panel/`: pages/forums.php, actions/delete_thread.php
- `cron.php`: Clean tasks
- `uploads/`: Media storage

#### Build Guidance:
- Build PHP backend, then Node.js for live features
- **Extensions**: File uploads
- **Outcomes**: Real-time integration, API design

### Project 3: Event Sharing Community Platform (Advanced Level)

Develop a site for events with social/monetization. **Focus**: Advanced queries, payments, notifications.

#### Key Features:
- Event creation (title/date/location)
- Feeds, RSVPs, comments
- Themed groups
- Premium event payments (e.g., Stripe)
- Notifications; admin analytics

#### Utilization of Structure:
- **PHP**: OOP models; Composer optional
- **Supporting**: JS for maps; Node.js for live
- **Database**: Tables: events, rsvps, groups, notifications

#### Mapping:
- `config.php`: API keys (Stripe/SMTP)
- `sources/`: event.php (create/get), notification.php (send)
- `requests/`: event.php (creation), group.php (display)
- `themes/default/layout/`: event_detail.php, notifications.php
- `xhr/`: rsvp_event.php
- `api/`: v1/create_event.php
- `assets/js/`: events.js (maps/updates)
- `nodejs/`: Live RSVPs
- `admin-panel/`: pages/analytics.php, actions/approve_event.php
- `cron.php`: Email queues
- `install.php`: Schema/sample data

#### Build Guidance:
- Start with CRUD, add social, then real-time/admin
- **Extensions**: Payments module
- **Outcomes**: Full-stack, scalability, extensibility

## 🚀 Getting Started

1. **Set up your development environment** (XAMPP, WAMP, etc.)
2. **Start with Project 1** to understand the basic structure
3. **Configure** config.php and database using install.php
4. **Build incrementally** following the guidance for each project
5. **Test locally** and implement security measures
6. **Extend with custom features** using the modular structure

---

**Ready to start building?** Begin with Project 1 and follow the structured approach to create your own social networking platform! 🚀
