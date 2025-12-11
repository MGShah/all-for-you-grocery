# All for You - Grocery Shop

A full-featured Django-based grocery shop website with admin dashboard, user authentication, shopping cart, and product management.

## Features

- 🏠 Beautiful landing page with product showcase
- 👤 User registration and login system
- 🛒 Shopping cart functionality
- 📦 Product catalog with categories
- 🔍 Product search and filtering
- 👨‍💼 Admin dashboard for managing:
  - Products and inventory
  - Categories
  - Orders
  - Customers
- 📱 Responsive design (mobile-friendly)
- 💳 Checkout system

## Tech Stack

- **Backend**: Django 4.2
- **Database**: MySQL
- **Frontend**: HTML, CSS, Bootstrap 5
- **Authentication**: Django built-in auth

## Installation

### Prerequisites

- Python 3.8+
- MySQL Server
- pip

### Setup Instructions

1. **Clone the repository**
```bash
git clone https://github.com/MGShah/all-for-you-grocery.git
cd all-for-you-grocery
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure MySQL Database**

Create a MySQL database:
```sql
CREATE DATABASE grocery_shop;
```

5. **Configure Environment Variables**

Create a `.env` file in the project root:
```
SECRET_KEY=your-secret-key-here
DEBUG=True
DB_NAME=grocery_shop
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_HOST=localhost
DB_PORT=3306
```

6. **Run Migrations**
```bash
python manage.py makemigrations
python manage.py migrate
```

7. **Create Superuser (Admin)**
```bash
python manage.py createsuperuser
```

8. **Run Development Server**
```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` to see the website.

## Admin Dashboard

Access the admin dashboard at `http://127.0.0.1:8000/admin/`

Use the superuser credentials you created to login.

## Project Structure

```
all-for-you-grocery/
├── manage.py
├── requirements.txt
├── grocery_shop/          # Main project settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── store/                 # Main application
│   ├── models.py         # Database models
│   ├── views.py          # View functions
│   ├── urls.py           # URL routing
│   ├── forms.py          # Forms
│   ├── admin.py          # Admin customization
│   └── templates/        # HTML templates
│       ├── base.html
│       ├── index.html
│       ├── products.html
│       ├── product_detail.html
│       ├── cart.html
│       ├── checkout.html
│       ├── login.html
│       └── register.html
└── static/               # CSS, JS, Images
    ├── css/
    ├── js/
    └── images/
```

## Usage

### For Customers:
1. Browse products on the homepage
2. Register/Login to your account
3. Add products to cart
4. Proceed to checkout
5. View order history

### For Admin:
1. Login to admin dashboard
2. Add/Edit/Delete products
3. Manage categories
4. View and manage orders
5. Manage customer accounts

## Deployment

For production deployment:

1. Set `DEBUG=False` in `.env`
2. Configure allowed hosts in `settings.py`
3. Use a production-ready database
4. Set up static files serving
5. Use gunicorn as WSGI server

## Download as ZIP

Click the green "Code" button → "Download ZIP" to get the complete project.

## License

MIT License

## Support

For issues or questions, please open an issue on GitHub.

---

**Built with ❤️ for "All for You" Grocery Shop**