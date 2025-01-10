
# Library Management System
## Features

### Authentication & Authorization
- User login and logout.
- Role-based access control (e.g., Admin, User).

### Book Management
- List all books.
- Add, edit, and delete books (admin-only features).
- Track book availability and borrowing status.

### Borrower Management
- View a list of borrowers.
- Borrow books by selecting available titles.
- Return borrowed books.

### Dashboard
- Role-specific dashboards for users and admins.

## Installation

### Requirements
- PHP 7.4 or higher.
- Composer.
- CodeIgniter 4 framework.
- MySQL or PostgreSQL database.

## **Langkah-Langkah Instalasi**
1. **Clone Repository**
   Clone repository ini ke komputer lokal Anda:
   ```bash
   git clone https://github.com/your-repository/library-final.git
   cd library-book-management
   ```

2. **Install Dependensi**
   Pastikan Composer sudah terinstal, lalu jalankan:
   ```bash
   composer install
   ```

3. **Konfigurasikan File `.env`**
   Salin file `.env.example` menjadi `.env`:
   ```bash
   cp .env.example .env
   ```
   Kredensial database default sudah diatur untuk menggunakan database yang telah di-*deploy*. Anda tidak perlu mengubahnya kecuali jika ingin menggunakan database Anda sendiri.

4. **Jalankan Server**
   Gunakan server bawaan PHP untuk menjalankan aplikasi:
   ```bash
   php spark serve
   ```
   Aplikasi dapat diakses di `http://localhost:8080/books`.

## Application Structure

### Controllers

#### AuthController
- Handles user authentication and registration.
- Methods:
  - `login`: Displays the login form.
  - `authenticate`: Validates credentials and logs in the user.
  - `logout`: Logs out the user.
  - `register`: Displays the registration form.
  - `storeUser`: Saves new user accounts.

#### BooksController
- Manages book records.
- Methods:
  - `index`: Lists all books.
  - `create`: Displays the form for adding a new book (admin-only).
  - `store`: Saves a new book to the database (admin-only).
  - `edit`: Displays the form for editing a book (admin-only).
  - `update`: Updates book details (admin-only).
  - `delete`: Deletes a book (admin-only).
  - `trackBook`: Displays book borrowing details.

#### BorrowerController
- Manages book borrowing and returns.
- Methods:
  - `listBorrowers`: Lists all borrower records.
  - `create`: Displays the form for borrowing a book.
  - `store`: Saves borrower details and updates book status.
  - `returnBook`: Handles book return and updates the status.

#### DashboardController
- Displays a role-specific dashboard.

### Routes
Defined in `app/Config/Routes.php`. Key routes include:

#### Authentication
- `GET /login`: Displays the login form.
- `POST /authenticate`: Authenticates the user.
- `GET /logout`: Logs out the user.
- `GET /register`: Displays the registration form.
- `POST /register`: Registers a new user.

#### Dashboard
- `GET /dashboard`: Displays the dashboard for logged-in users.

#### Books
- `GET /books`: Lists all books.
- `GET /books/create`: Displays the form to add a new book (admin-only).
- `POST /books/store`: Saves a new book to the database (admin-only).
- `GET /books/edit/(:num)`: Displays the form to edit a book (admin-only).
- `POST /books/update/(:num)`: Updates a book's details (admin-only).
- `DELETE /books/(:num)`: Deletes a book (admin-only).
- `GET /books/track/(:num)`: Displays borrowing details for a book.

#### Borrowers
- `GET /borrowers`: Lists all borrower records.
- `GET /borrowers/create`: Displays the form to borrow a book.
- `POST /borrowers`: Saves a new borrower record.
- `POST /borrowers/return/(:num)`: Handles returning a borrowed book.

## Usage

### Admin Features
- Log in as an admin.
- Add, edit, and delete books.
- View and manage borrower records.

### User Features
- Log in as a user.
- Borrow books from the available list.
- Return borrowed books.

## Validation Rules
- User registration:
  - Username: Required, unique, minimum 3 characters.
  - Password: Required, minimum 6 characters.
  - Role: Must be `user` or `admin`.
- Book management:
  - Title, Author, and Category: Required, minimum 3 characters.
  - Status: Must be `available` or `borrowed`.
- Borrower management:
  - Name: Required, minimum 3 characters.
  - Book ID: Must reference an existing book.
  - Borrow Date, Return Date: Valid date format.



