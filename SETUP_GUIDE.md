# All for You - Complete Setup Guide

## 📥 Download the Project

**Option 1: Download ZIP**
1. Go to: https://github.com/MGShah/all-for-you-grocery
2. Click the green "Code" button
3. Click "Download ZIP"
4. Extract the ZIP file to your desired location

**Option 2: Clone with Git**
```bash
git clone https://github.com/MGShah/all-for-you-grocery.git
cd all-for-you-grocery
```

## 🔧 Prerequisites

Before starting, make sure you have:
- Python 3.8 or higher installed
- MySQL Server installed and running
- pip (Python package manager)

### Check Python Installation
```bash
python --version
# or
python3 --version
```

### Install MySQL
- **Windows**: Download from https://dev.mysql.com/downloads/installer/
- **Mac**: `brew install mysql`
- **Linux**: `sudo apt-get install mysql-server`

## 📦 Step-by-Step Installation

### 1. Create Virtual Environment
```bash
# Navigate to project directory
cd all-for-you-grocery

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate

# On Mac/Linux:
source venv/bin/activate
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Setup MySQL Database

**Start MySQL and create database:**
```bash
# Login to MySQL
mysql -u root -p

# Create database
CREATE DATABASE grocery_shop;

# Create user (optional but recommended)
CREATE USER 'grocery_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON grocery_shop.* TO 'grocery_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

### 4. Configure Environment Variables

**Create `.env` file in project root:**
```bash
# Copy the example file
cp .env.example .env

# Edit .env file with your settings
```

**Edit `.env` file:**
```
SECRET_KEY=your-secret-key-here-generate-a-random-one
DEBUG=True

DB_NAME=grocery_shop
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_HOST=localhost
DB_PORT=3306
```

**Generate SECRET_KEY:**
```python
# Run this in Python shell
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

### 5. Run Database Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create Superuser (Admin)
```bash
python manage.py createsuperuser

# Follow prompts:
# Username: admin
# Email: admin@allforyou.com
# Password: (choose a strong password)
```

### 7. Collect Static Files
```bash
python manage.py collectstatic --noinput
```

### 8. Run Development Server
```bash
python manage.py runserver
```

**Visit:** http://127.0.0.1:8000/

## 🎉 You're Done!

### Access Points:
- **Website**: http://127.0.0.1:8000/
- **Admin Dashboard**: http://127.0.0.1:8000/admin/
  - Login with superuser credentials

## 📝 Adding Sample Data

### Via Admin Dashboard:
1. Go to http://127.0.0.1:8000/admin/
2. Login with superuser credentials
3. Add Categories (e.g., Fruits, Vegetables, Dairy)
4. Add Products with images, prices, descriptions

### Via Django Shell (Optional):
```bash
python manage.py shell
```

```python
from store.models import Category, Product

# Create categories
fruits = Category.objects.create(name="Fruits", description="Fresh fruits")
vegetables = Category.objects.create(name="Vegetables", description="Fresh vegetables")

# Create products
Product.objects.create(
    category=fruits,
    name="Apple",
    description="Fresh red apples",
    price=120,
    discount_price=100,
    stock=50,
    unit="kg",
    featured=True
)

Product.objects.create(
    category=vegetables,
    name="Tomato",
    description="Fresh tomatoes",
    price=40,
    stock=100,
    unit="kg",
    featured=True
)
```

## 🚀 Features Overview

### Customer Features:
- ✅ Browse products by category
- ✅ Search products
- ✅ User registration and login
- ✅ Add products to cart
- ✅ Update cart quantities
- ✅ Checkout and place orders
- ✅ View order history
- ✅ Manage profile

### Admin Features:
- ✅ Manage products (add/edit/delete)
- ✅ Manage categories
- ✅ View and update orders
- ✅ Manage customers
- ✅ Track inventory
- ✅ Update order status

## 🎨 Customization

### Change Colors:
Edit `store/templates/store/base.html` and modify CSS variables:
```css
:root {
    --primary-color: #2ecc71;  /* Change this */
    --secondary-color: #27ae60; /* Change this */
}
```

### Add Logo:
1. Place logo image in `static/images/logo.png`
2. Update navbar in `base.html`

### Modify Homepage:
Edit `store/templates/store/index.html`

## 🐛 Troubleshooting

### MySQL Connection Error:
```
django.db.utils.OperationalError: (2002, "Can't connect to MySQL server")
```
**Solution**: Make sure MySQL is running and credentials in `.env` are correct

### Module Not Found:
```
ModuleNotFoundError: No module named 'mysqlclient'
```
**Solution**: 
```bash
pip install mysqlclient
# If fails on Windows, try:
pip install pymysql
# Then add to grocery_shop/__init__.py:
import pymysql
pymysql.install_as_MySQLdb()
```

### Static Files Not Loading:
```bash
python manage.py collectstatic --noinput
```

### Port Already in Use:
```bash
# Use different port
python manage.py runserver 8080
```

## 📱 Production Deployment

### For Railway/Heroku:
1. Set `DEBUG=False` in `.env`
2. Update `ALLOWED_HOSTS` in `settings.py`
3. Use production database (not SQLite)
4. Configure static files serving
5. Use gunicorn (already in requirements.txt)

### Environment Variables for Production:
```
SECRET_KEY=production-secret-key
DEBUG=False
DB_NAME=production_db
DB_USER=production_user
DB_PASSWORD=strong_password
DB_HOST=your-db-host
```

## 📞 Support

For issues:
1. Check this guide
2. Review Django documentation
3. Check MySQL connection
4. Verify all dependencies installed

## 🎯 Next Steps

1. Add product images via admin
2. Create categories
3. Add products
4. Test the complete flow:
   - Register user
   - Browse products
   - Add to cart
   - Checkout
   - View orders

---

**Enjoy your grocery shop! 🛒**