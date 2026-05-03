# TKS PHP Telegram Login

A lightweight PHP and MySQL example for signing users in with the Telegram Login Widget. The app verifies Telegram authorization data, creates or updates the user in MySQL, stores the logged-in Telegram ID in a PHP session, and displays the authenticated user's profile.

## Features

- Telegram Login Widget integration
- Telegram HMAC authorization check
- User create/update flow in MySQL
- PHP session-based login state
- Simple user profile and logout pages

## Requirements

- PHP 7.4 or newer with PDO enabled
- MySQL or MariaDB
- A Telegram bot created with BotFather
- A web server such as Apache, Nginx, or PHP's built-in development server

## Project Structure

```text
.
+-- assets/
|   +-- style.css
+-- database/
|   +-- table-structure.sql
+-- auth.php
+-- db-config.php
+-- login.php
+-- logout.php
+-- user.php
```

## Setup

1. Clone or download this repository.

2. Create a MySQL database named `telegram_login`.

3. Import the table structure:

   ```sql
   SOURCE database/table-structure.sql;
   ```

   You can also import `database/table-structure.sql` through phpMyAdmin or another database client.

4. Update the database connection in `db-config.php`:

   ```php
   $db = new Database(
       "127.0.0.1",
       "telegram_login",
       "root",
       ""
   );
   ```

5. Create a Telegram bot with BotFather and configure your domain for Telegram Login.

6. Update the bot username in `login.php`:

   ```php
   define('BOT_USERNAME', 'your_bot_username');
   ```

7. Update the bot token in `auth.php`:

   ```php
   define('BOT_TOKEN', 'your_bot_token');
   ```

8. Serve the project from your web server and open `login.php` in the browser.

## Development Server

For local testing, you can run PHP's built-in server from the project root:

```bash
php -S localhost:8000
```

Then visit:

```text
http://localhost:8000/login.php
```

Telegram Login requires a properly configured bot/domain, so full authentication may require hosting the project on the configured domain.

## Security Notes

- Do not commit real bot tokens, database passwords, or production secrets.
- Use HTTPS in production.
- Move credentials to environment variables or a private local config file before deploying a real application.
- Validate and escape any user-facing output before extending this project for production use.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
