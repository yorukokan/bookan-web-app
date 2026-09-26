<div align="center">

  <h1>📖 Bookan - Social Book Discovery & Management Platform</h1>
  <p><strong>A social web platform designed for book enthusiasts to manage personal libraries, share impactful quotes, and discover new literary works.</strong></p>

  <!-- Badges -->
  <p>
    <img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP" />
    <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL" />
    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
    <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
    <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
    <img src="https://img.shields.io/badge/XAMPP-FB7A24?style=for-the-badge&logo=xampp&logoColor=white" alt="XAMPP" />
    <img src="https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge" alt="License" />
  </p>

</div>

---

## 📌 Project Overview

**Bookan** is an interactive, community-driven web application tailored for readers. Instead of reading in isolation, Bookan transforms reading into a dynamic, shared experience. 

Users can curate their personal bookshelves, catalog books with rich metadata, quote and highlight memorable sentences, and interact with other passionate readers. With role-based session controls, public visitors can explore books and community quotes, while registered members unlock full interactive capabilities such as commenting, liking, saving favorites, and publishing quotes.

---

## ✨ Key Features & Modules

### 🔐 1. Authentication & Session Management
* **Secure Registration & Login:** User credentials securely managed with salted password hashing.
* **PHP Session Control:** Persistent session handling with page-level access restriction for unauthorized visitors.
* **Role/Permission Scoping:** Guest mode for reading and browsing; authenticated mode for active social participation.

### 📚 2. Personal Library & Book Management
* **Comprehensive Book Cataloging:** Add, update, and manage books with complete metadata (Title, Author, Publisher, Publication Year, Category/Genre, ISBN, and Cover Image).
* **Reading Status Tracking:** Organize books by personal progress (e.g., *Want to Read*, *Currently Reading*, *Finished*).
* **Categorization:** Filter and organize books by literary genre and themes.

### 💬 3. Social Quote Sharing (Alıntı Akışı)
* **Passage Sharing:** Post impactful quotes directly referenced to specific books and page numbers.
* **Discovery Feed:** Real-time community stream showcasing recent quotes shared by fellow readers.

### ❤️ 4. Community & Interactive Engagement
* **Favorites System:** Save favorite books and inspiring quotes into dedicated personal lists for fast access.
* **Social Reactions:** Like quotes and participate in discussion threads via interactive comment sections.
* **User Profiles:** Personalized public profile pages showcasing individual libraries, reading activity, and shared quotations.

### 🔍 5. Dynamic Search & Filtering
* Instant search capability across book titles, authors, categories, and quote contents.

---

## 🛠 Tech Stack & Architecture

| Layer | Technology | Role & Function |
| :--- | :--- | :--- |
| **Backend** | Native PHP (7.4+ / 8.x) | Core business logic, session handling, request routing, and data processing |
| **Database** | MySQL | Relational database management system with structured relational tables |
| **Frontend** | HTML5, CSS3, JavaScript | Responsive user interface, asynchronous UI events, and DOM manipulation |
| **Local Environment** | XAMPP / AppServ (Apache) | Local server deployment, MySQL daemon, and phpMyAdmin database management |

---

## 🗄 Database Design (Relational Schema)

The MySQL database incorporates relational constraints to ensure data integrity:

* `users`: Stores user credentials, email, profile details, and account creation timestamps.
* `books`: Catalogs book details including title, author, category_id, publisher, publication year, and cover image path.
* `categories`: Master table for book genres and classification.
* `quotes`: Stores user-submitted quotations linked to `users` and `books`.
* `favorites`: User-book and user-quote bookmark relations.
* `likes`: Many-to-many relationship mapping user likes to specific quotes.
* `comments`: Discussion threads linked to quotes with author references.

---

## 📂 Project Structure

```plaintext
bookan-web/
├── config/
│   └── db.php               # Database connection configuration (PDO / MySQLi)
├── assets/
│   ├── css/                 # Stylesheets (style.css, responsive.css)
│   ├── js/                  # Interactive client-side scripts (main.js)
│   └── images/              # Static branding and interface assets
├── includes/
│   ├── header.php           # Common navigation bar and header template
│   ├── footer.php           # Common footer template
│   └── auth_check.php       # Session verification and route protection
├── uploads/                 # Uploaded book covers and user profile avatars
├── sql/
│   └── bookan_db.sql        # Database schema creation and initial seeding scripts
├── index.php                # Homepage and global community feed
├── login.php                # Member sign-in page
├── register.php             # New account registration page
├── logout.php               # Session termination script
├── profile.php              # User profile, personal library, and quotes
├── book_detail.php          # Book detail view and associated quotes
├── add_book.php             # Book submission form
├── add_quote.php            # Quote creation form
└── README.md
```

---

## 🚀 Setup & Local Installation

Follow these steps to run the application locally using **XAMPP** or **AppServ**:

### Prerequisites

* Modern web browser (Chrome, Firefox, Safari, Edge)
* [XAMPP](https://www.apachefriends.org/) or [AppServ](https://www.appserv.org/) installed on your machine

### Installation Steps

1. **Deploy Project to Web Server Root:**
   * Clone or copy the project folder into your local server web directory:
     * **XAMPP:** `C:/xampp/htdocs/bookan-web`
     * **AppServ:** `C:/AppServ/www/bookan-web`

2. **Database Import:**
   * Start **Apache** and **MySQL** from your XAMPP or AppServ control panel.
   * Open your browser and navigate to `http://localhost/phpmyadmin`.
   * Create a new database named `bookan_db` with collation `utf8mb4_unicode_ci`.
   * Click **Import** and select `sql/bookan_db.sql` from the project repository.

3. **Database Configuration:**
   * Edit `config/db.php` to verify your local database credentials:
     ```php
     <?php
     $host = "localhost";
     $user = "root";
     $pass = ""; // Default is empty for XAMPP; enter your AppServ password if set
     $db   = "bookan_db";

     try {
         $conn = new PDO("mysql:host=$host;dbname=$db;charset=utf8mb4", $user, $pass);
         $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
     } catch (PDOException $e) {
         die("Database connection failed: " . $e->getMessage());
     }
     ?>
     ```

4. **Run the Application:**
   * Open your browser and go to:
     ```text
     http://localhost/bookan-web
     ```

---

## 🔒 Security Best Practices

* **Prepared Statements:** Prevents SQL Injection by leveraging parameterized PDO queries for all user inputs.
* **XSS Protection:** Neutralizes Cross-Site Scripting threats using `htmlspecialchars()` encoding on all dynamic outputs.
* **Password Hashing:** Secures user passwords using modern bcrypt cryptographic hashing via PHP's `password_hash()`.

---


