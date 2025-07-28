# PHP-Based Social Networking Project Guide

A structured approach to building modular social networking applications using custom PHP patterns inspired by scripts like WoWonder. Create extensible and secure web applications without relying on heavy frameworks.

## 🚀 Features

- **Modular Architecture**: Clean separation of concerns with MVC-like structure
- **Security First**: Built-in CSRF protection, password hashing, and input sanitization
- **Real-time Capabilities**: WebSocket integration with Node.js and Socket.io
- **Extensible Design**: Plugin and theme system for customization
- **Progressive Learning**: Three projects from beginner to advanced level

## 📋 Prerequisites

- PHP 7.4+ or 8.x
- MySQL database
- Basic understanding of PHP fundamentals (variables, functions, sessions, OOP)
- Local development environment (XAMPP, WAMP, or similar)

### Supporting Technologies

- **JavaScript** (vanilla or jQuery) for front-end interactivity and AJAX
- **HTML/CSS** with Bootstrap-inspired responsive styles
- **Node.js** with Socket.io for real-time features
- **MySQL** for database operations
- **Composer** (optional) for dependency management

## 🏗️ Project Structure

```
my-social-project/
├── assets/                     # Static resources
│   ├── js/                     # JavaScript files
│   ├── css/                    # Stylesheets
│   └── img/                    # Default images
├── uploads/                    # User-uploaded media
├── themes/                     # Modular themes
│   └── default/
│       ├── layout/             # PHP/HTML views
│       ├── javascript/         # Theme-specific JS
│       ├── stylesheet/         # Theme CSS
│       └── img/               # Theme images
├── xhr/                        # AJAX handlers
├── requests/                   # Controllers
├── sources/                    # Models and utilities
├── admin-panel/               # Admin dashboard
│   ├── pages/                 # Admin views
│   ├── actions/               # Admin controllers
│   └── assets/                # Admin JS/CSS
├── api/                       # RESTful API endpoints
├── nodejs/                    # Real-time server
├── includes/                  # Third-party libraries
├── config.php                 # Central configuration
├── functions.php              # Global helper functions
├── install.php                # Setup script
├── index.php                  # Main entry point
├── .htaccess                  # URL rewriting rules
├── cron.php                   # Background tasks
└── database.sql               # Database schema
```

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/php-social-network.git
   cd php-social-network
   ```

2. **Set up your web server**
   - Place the project in your web server directory
   - Ensure PHP and MySQL are running

3. **Configure the database**
   - Create a new MySQL database
   - Import the `database.sql` file

4. **Run the installer**
   - Navigate to `http://localhost/your-project/install.php`
   - Follow the setup wizard

5. **Configure settings**
   - Update `config.php` with your database credentials
   - Set up any required API keys

## 🔒 Security Best Practices

- ✅ Use prepared statements (PDO/MySQLi)
- ✅ Hash passwords with `password_hash()`
- ✅ Sanitize all inputs
- ✅ Implement CSRF tokens
- ✅ Secure file uploads
- ✅ Validate user permissions

## 📚 Learning Projects

### Project 1: Basic Social Profile Network (Beginner)

**Features:**
- User registration and authentication
- Profile creation and editing
- Text posts with likes and comments
- Follow/unfollow system
- Basic admin panel

**Focus:** Authentication, CRUD operations, basic social features

### Project 2: Real-Time Chat Forum (Intermediate)

**Features:**
- User search and friend requests
- Public forums with threads and replies
- Real-time messaging system
- Media uploads in chats
- Admin moderation tools

**Focus:** Real-time features, APIs, asynchronous operations

### Project 3: Event Sharing Community Platform (Advanced)

**Features:**
- Event creation and management
- RSVP system with notifications
- Themed community groups
- Payment integration (Stripe)
- Advanced admin analytics

**Focus:** Complex queries, payment processing, advanced notifications

## 🚀 Getting Started

1. **Start with Project 1** to understand the basic structure
2. **Configure your environment** following the installation guide
3. **Build incrementally** - authentication first, then features
4. **Test locally** before deploying
5. **Extend with plugins** and custom themes

## 📖 Code Examples

### Basic User Authentication
```php
// sources/user.php
class User {
    public static function register($username, $password, $email) {
        $hashed_password = password_hash($password, PASSWORD_DEFAULT);
        // Database insertion with prepared statements
    }
    
    public static function login($username, $password) {
        // Verify credentials and start session
    }
}
```

### AJAX Handler Example
```php
// xhr/like_post.php
if ($_POST['action'] == 'like_post') {
    $post_id = (int)$_POST['post_id'];
    $user_id = $_SESSION['user_id'];
    
    // Toggle like status
    $result = Post::toggleLike($post_id, $user_id);
    echo json_encode(['status' => 'success', 'likes' => $result]);
}
```

## 🔄 Real-time Features

The project includes Node.js integration for real-time features:

```javascript
// nodejs/server.js
const io = require('socket.io')(server);

io.on('connection', (socket) => {
    socket.on('send_message', (data) => {
        // Broadcast message to specific users
        socket.broadcast.emit('new_message', data);
    });
});
```

## 🎨 Theming System

Create custom themes by copying the default theme structure:

```
themes/
├── default/
└── your-custom-theme/
    ├── layout/
    ├── stylesheet/
    └── javascript/
```

## 📊 Database Schema

Key tables include:
- `users` - User accounts and profiles
- `posts` - User posts and content
- `follows` - User relationships
- `messages` - Private messaging
- `events` - Event management
- `notifications` - System notifications

## 🔧 Configuration

Update `config.php` with your settings:

```php
// Database configuration
define('DB_HOST', 'localhost');
define('DB_NAME', 'your_database');
define('DB_USER', 'your_username');
define('DB_PASS', 'your_password');

// Site configuration
define('SITE_URL', 'http://localhost/your-project/');
define('UPLOAD_PATH', 'uploads/');
```

## 🤝 Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- Create an [issue](https://github.com/yourusername/php-social-network/issues) for bug reports
- Join our [community discussions](https://github.com/yourusername/php-social-network/discussions)
- Check the [wiki](https://github.com/yourusername/php-social-network/wiki) for detailed documentation

## 🙏 Acknowledgments

- Inspired by WoWonder and similar social networking scripts
- Built with modern PHP best practices
- Community-driven development approach

---

**Ready to build your social network?** Start with Project 1 and work your way up! 🚀
