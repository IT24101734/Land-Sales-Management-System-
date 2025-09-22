# Land Sales Management System 
A comprehensive web-based property sales management system built with PHP and MySQL. Features user authentication, property listings, admin dashboard, and integrated payment processing for real estate transactions in Sri Lanka.
# 🏡 Dream Property Sales - Land Sales Management System

A comprehensive web-based property sales management system built with PHP and MySQL. This platform enables users to browse, list, and manage property sales with an integrated payment system, specifically designed for the Sri Lankan real estate market.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PHP](https://img.shields.io/badge/PHP-7.0%2B-blue.svg)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-orange.svg)](https://mysql.com)

## 🌟 Key Features

### 👥 User Management
- **User Registration & Authentication** - Secure signup and login system
- **Profile Management** - Users can view and edit their profiles
- **Session Management** - Secure session handling
- **Role-based Access** - Different access levels for users and admins

### 🏞️ Property Management
- **Property Listings** - Browse available land properties with detailed information
- **Add New Listings** - Registered users can add their properties
- **Image Upload** - Upload and display property images
- **Location-based Search** - Properties categorized by Sri Lankan districts
- **Detailed Property Info** - Title, description, size (in perches), price per perch, location

### 🔧 Admin Panel
- **User Management** - View, edit, and delete user accounts
- **Property Management** - Manage all property listings
- **Payment Tracking** - Monitor payment transactions
- **Inquiry Management** - Handle user inquiries

### 💳 Payment System
- **Multiple Payment Methods** - PayPal, VISA, MasterCard support
- **Listing Fees** - Pay-per-day property listing system (100 LKR/day)
- **Secure Transactions** - Safe payment processing
- **Payment History** - Track all payment transactions

### 🎨 User Interface
- **Responsive Design** - Mobile-friendly interface
- **Modern UI** - Clean and intuitive design
- **Easy Navigation** - User-friendly menu system
- **Rich Content** - About us, services, and contact pages

## 🛠️ Technology Stack

- **Backend:** PHP 7.0+
- **Database:** MySQL 5.7+
- **Frontend:** HTML5, CSS3, JavaScript
- **Styling:** Custom CSS with responsive design
- **File Upload:** PHP file handling for images
- **Session Management:** PHP sessions

## 📁 Project Structure

```
Land-sales-management-system/
├── index.php              # Homepage
├── login.php              # User login
├── register.php           # User registration
├── lands.php              # Property listings
├── addLand.php            # Add new property
├── payment.php            # Payment processing
├── profile.php            # User profile
├── connect.php            # Database connection
├── admin/                 # Admin panel
│   ├── manageuser.php     # User management
│   ├── manageland.php     # Property management
│   ├── managepayment.php  # Payment management
│   └── inquire.php        # Inquiry management
├── styles/                # CSS stylesheets
├── script/                # JavaScript files
├── images/                # Static images
└── lands/                 # Uploaded property images
```

## 🚀 Installation

### Prerequisites
- **XAMPP/WAMP/LAMP** server environment
- **PHP 7.0+** 
- **MySQL 5.7+**
- **Web browser** (Chrome, Firefox, Safari, Edge)

### Step 1: Clone the Repository
```bash
git clone https://github.com/gawrawat/Land-sales-management-system.git
cd Land-sales-management-system
```

### Step 2: Database Setup
1. Start your MySQL server (via XAMPP/WAMP)
2. Create a new database named `land_sale`
3. Import the database schema (you'll need to create tables for):
   - `user` (id, name, email, phone, username, password)
   - `lands` (land_Id, title, description, city, address, size, price, fileName, s_Id)
   - `payment` (id, hoderName, cNumber, cvv, exp, method, amount, UserId)

### Step 3: Configure Database Connection
1. Open `connect.php`
2. Update database credentials:
```php
$server = 'localhost';
$sUsername = 'root';      // Your MySQL username
$sPassword = '';          // Your MySQL password
$DBname = 'land_sale';    // Database name
```

### Step 4: Set Permissions
Ensure the `lands/` directory has write permissions for file uploads:
```bash
chmod 755 lands/
```

### Step 5: Access the Application
1. Place the project in your web server directory (`htdocs` for XAMPP)
2. Start Apache and MySQL services
3. Open browser and navigate to: `http://localhost/Land-sales-management-system/`

## 📖 Usage Guide

### For Users:
1. **Register** an account or **Login** with existing credentials
2. **Browse Properties** on the lands page
3. **Add Property** by clicking "Add Land" (requires login)
4. **Make Payment** for property listing (100 LKR per day)
5. **Manage Profile** through the profile page

### For Administrators:
1. **Login** with admin credentials (username: `admin`, password: `admin`)
2. **Manage Users** - View, edit, or delete user accounts
3. **Manage Properties** - Oversee all property listings
4. **Track Payments** - Monitor payment transactions
5. **Handle Inquiries** - Respond to user inquiries

## 🏙️ Supported Cities (Sri Lanka)

The system supports property listings in all major Sri Lankan districts:
- Colombo, Gampaha, Kalutara
- Kandy, Matale, Nuwara Eliya
- Galle, Matara, Hambantota
- And 15+ more districts

## 🔐 Security Features

- **SQL Injection Protection** - Parameterized queries
- **Session Security** - Secure session management
- **File Upload Validation** - Image file type verification
- **Admin Access Control** - Separate admin authentication
- **Password Protection** - User password security

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Development Guidelines:
- Follow PHP PSR standards
- Add comments for complex logic
- Test all features before submitting
- Update documentation when needed

## 📝 Database Schema

### Users Table
```sql
CREATE TABLE user (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(15),
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL
);
```

### Lands Table
```sql
CREATE TABLE lands (
    land_Id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(200) NOT NULL,
    description TEXT,
    city VARCHAR(50),
    address TEXT,
    size DECIMAL(10,2),
    price DECIMAL(10,2),
    fileName VARCHAR(255),
    s_Id INT,
    FOREIGN KEY (s_Id) REFERENCES user(id)
);
```

### Payment Table
```sql
CREATE TABLE payment (
    id INT PRIMARY KEY AUTO_INCREMENT,
    hoderName VARCHAR(100),
    cNumber VARCHAR(20),
    cvv VARCHAR(4),
    exp VARCHAR(10),
    method VARCHAR(20),
    amount DECIMAL(10,2),
    UserId INT,
    FOREIGN KEY (UserId) REFERENCES user(id)
);
```

## 🐛 Known Issues

- Password encryption could be improved (consider bcrypt)
- File upload size limits may need adjustment
- Payment gateway integration is simulated (not connected to real processors)

## 🔄 Future Enhancements

- [ ] **Advanced Search** - Filter by price range, size, location
- [ ] **Property Comparison** - Compare multiple properties
- [ ] **Email Notifications** - Automated email alerts
- [ ] **Google Maps Integration** - Property location mapping
- [ ] **Mobile App** - React Native or Flutter app
- [ ] **Real Payment Gateway** - Stripe/PayPal integration
- [ ] **Property Reviews** - User rating system
- [ ] **Advanced Analytics** - Dashboard with insights

## 📞 Support

For support and queries:
- **Email:** dreamproperties@info.com
- **Phone:** +94 11 265 9842
- **Address:** 22/4, Vihaara Mawatha, Malabe, Colombo

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Gawrawat**
- GitHub: [@gawrawat](https://github.com/gawrawat)

## 🙏 Acknowledgments

- Thanks to all contributors who helped shape this project
- Inspired by modern real estate platforms
- Built for the Sri Lankan property market
- Special thanks to the PHP and MySQL communities

---

⭐ **Star this repo** if you find it helpful! 

🔗 **Share** with others who might benefit from this property management system!

---

*Last updated: September 2025*
