# Waste-Management-System
A web-based platform for citizens to report waste and garbage issues to their municipality, track complaint status, and learn about proper waste management practices. The system includes user authentication with email verification, complaint submission with image upload, and an admin panel for managing complaints.

## Features

- **User Authentication**
  - Registration with email verification (OTP code)
  - Secure login/logout with password hashing
  - Password reset via email OTP
- **Complaint Management**
  - Submit complaints with waste type, location, description, and optional image
  - Track complaint status (Pending / Completed)
- **Informative Pages**
  - About Us, FAQ, waste statistics, and guidelines
- **Admin Panel**
  - Separate admin login
  - View and update complaint status
- **Responsive Design**
  - Mobile-friendly layout using Bootstrap 4
  - Animated waves header on login page

## Technologies Used

- **Frontend**: HTML5, CSS3, Bootstrap 4, JavaScript (AOS, GLightbox, Swiper)
- **Backend**: PHP 7.2+, MySQL
- **Libraries**: Font Awesome, Google Fonts
- **Email**: PHP `mail()` function for OTP and reset codes
- **Database**: MySQL (provided `wms.sql`)

## Prerequisites

- Web server (Apache/Nginx) with PHP and MySQL
- PHP 7.2 or higher
- MySQL 5.7 or higher
- SMTP server or local mail configuration for email features (if using PHP `mail()`)

## Installation

1. **Clone or download** the project files to your web root directory (e.g., `htdocs` for XAMPP).

2. **Create a database** named `wms` (or any name you prefer).

3. **Import the database** using the provided `wms.sql` file:
   ```sql
   mysql -u root -p wms < wms.sql
Or use phpMyAdmin to import the file.

Configure database connection
Edit connection.php and update the database credentials if necessary:

php
$con = mysqli_connect('localhost', 'root', '', 'wms');
Configure email settings
In controllerUserData.php, update the $sender email addresses (lines containing bistajanak303@gmail.com and janak.bista@sagarmatha.edu.np) to your own email. Ensure PHP's mail() function is working on your server. For production, consider using PHPMailer with SMTP.

Set up admin panel
The SQL file includes an adminlogin table with sample credentials:

Username: admin, Password: admintest

Username: janak, Password: adminjanak
You can access the admin login via adminsignup/adminlogin.php (this file is not included in the provided set, so you may need to create it or use the existing references).

File permissions
Ensure the upload directory (e.g., for complaint images) is writable. The complaint form action points to phpGmailSMTP/trash.php – verify that this script exists and the upload path is correctly configured.

File Structure
text
/
├── assets/
│   ├── css/
│   │   └── style.css          # Main template styles
│   ├── img/                    # Images (clients, hero, etc.)
│   ├── js/
│   │   └── main.js             # Template JavaScript
│   └── vendor/                 # Third-party libraries (Bootstrap, AOS, etc.)
├── adminlogin/                  # Admin area (not fully provided)
├── phpGmailSMTP/                # Complaint handling scripts (referenced)
├── connection.php               # Database connection
├── controllerUserData.php       # Core authentication logic
├── forgot-password.php          # Password reset request form
├── index.html                   # Public homepage
├── login-user.php               # User login form (with waves header)
├── logout-user.php              # Logout and session destroy
├── new-password.php             # Set new password after OTP
├── password-changed.php         # Confirmation after password change
├── reset-code.php               # OTP entry for password reset
├── signup-user.php              # User registration form
├── style.css                    # Additional styles for login/signup forms
├── user-otp.php                 # OTP verification after signup
├── wavestyle.css                # CSS for waves animation on login header
└── wms.sql                      # Database dump
Usage
User Side
Navigate to the application URL.

Click Get Started or go to the login page.

Register as a new user (email verification required).

Log in with your verified email.

From the homepage, click Complain to file a report.

Fill in waste type, location, description, and optionally upload an image.

Use the Preview Complain link to check the status of your complaints (note: this currently links to the admin panel; user-specific complaint listing may need to be implemented).

Explore the About Us and FAQ sections for information on waste management.

Admin Side
Access admin login via the Login As Admin link at the bottom of the user login page, or directly via adminsignup/adminlogin.php.

Use the sample credentials from the adminlogin table.

View and manage complaints, update their status (Pending/Completed).

Database Tables
usertable: Stores registered users (id, name, email, password, code, status).

garbageinfo: Stores complaints (Id, name, mobile, email, wastetype, location, locationdescription, file, date, status).

adminlogin: Simple admin credentials (Id, username, password) – note: passwords are stored in plain text; consider hashing for production.

adminlogin_tbl: Another admin table with hashed passwords and email verification (id, name, email, password, code, status).

contact: Stores contact form submissions.

Customization
Styling: Modify colors, fonts, and layout in style.css, wavestyle.css, and the main assets/css/style.css.

Email Sender: Update the $sender email addresses in controllerUserData.php.

Waves Effect: Adjust animation parameters in wavestyle.css (e.g., speed, height).

Content: Add or edit FAQ items in index.html.

Troubleshooting
Email not sending: PHP mail() may not work on localhost without a mail server. Configure an SMTP library (e.g., PHPMailer) or use a testing tool like Mailtrap.

OTP verification fails: Check that the code field in usertable is being updated correctly. Ensure database connection is working.

File upload not working: Verify that the target PHP script (e.g., phpGmailSMTP/trash.php) exists and the upload directory has write permissions.

Login errors: Confirm that passwords are hashed correctly in the database. The controllerUserData.php uses password_hash() and password_verify().

Credits
Waves effect adapted from Simple CSS Waves by Goodkatz.

Bootstrap template based on Arsha.

Developed by Kartik and CO. (as per footer).

License
This project is open-source and available for educational purposes. Feel free to modify and use it according to your needs.

text
