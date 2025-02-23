# Backend Developer Assignment – User Data Management & Twitter OAuth API

## Overview
This project is a Symfony-based backend that manages user data from a CSV file and integrates Twitter OAuth authentication. It includes API endpoints for user management, database backup/restore, and Twitter authentication.

## Technology Stack
- **Language:** PHP
- **Framework:** Symfony
- **Database:** MySQL
- **Authentication:** Twitter OAuth 1.0a
- **Email Service:** Symfony Mailer with Mailgun

---

## **API Endpoints**

### **Part 1: User Data Management API**

#### 1. Upload and Store Data API
- **Endpoint:** `POST /api/upload`
- **Description:** Allows an admin to upload a CSV file containing user details.
- **Functionality:**
  - Parses the uploaded `data.csv` file.
  - Saves user data into the MySQL database.
  - Sends an email notification to each user asynchronously.

#### 2. View Data API
- **Endpoint:** `GET /api/users`
- **Description:** Retrieves all stored user data.

#### 3. Backup Database API
- **Endpoint:** `GET /api/backup`
- **Description:** Allows an admin to generate a backup of the database as `backup.sql`.

#### 4. Restore Database API
- **Endpoint:** `POST /api/restore`
- **Description:** Restores the database using a provided `backup.sql` file.

---

### **Part 2: Twitter OAuth Integration**

#### 1. Initiate Twitter Authentication
- **Endpoint:** `GET /auth/twitter`
- **Description:** Redirects the user to Twitter for authentication.

#### 2. Handle Twitter Callback
- **Endpoint:** `GET /auth/twitter/callback`
- **Description:** Handles the OAuth response, fetches user details, stores them in MySQL, and redirects the user back to the app.

---

## **Installation & Setup**

### **1. Clone the Repository**
```sh
git clone <repository-url>
cd backend
```
### **2. Install the dependencies**
```sh
composer install
```
### **3. Set Up enviorment variables**

```sh
DATABASE_URL="mysql://username:password@127.0.0.1:3306/db_name"
MAILER_DSN=smtp://your-smtp-server
TWITTER_CLIENT_ID=your_twitter_client_id
TWITTER_CLIENT_SECRET=your_twitter_client_secret

```
### **4. Run database migration**

```sh
php bin/console doctrine:migrations:migrate

```

### **5. Start symfony server**

```sh
symfony server:start
```
###  or you can start PHP server**

```sh
php -S 127.0.0.1:8000 -t public
