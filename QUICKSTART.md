# ⚡ Quick Start Guide

## 🎯 Get Running in 5 Minutes!

### 1️⃣ Download
```bash
# Download ZIP from GitHub or clone:
git clone https://github.com/MGShah/all-for-you-grocery.git
cd all-for-you-grocery
```

### 2️⃣ Setup Virtual Environment
```bash
python -m venv venv

# Windows:
venv\Scripts\activate

# Mac/Linux:
source venv/bin/activate
```

### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Setup Database
```bash
# Create MySQL database
mysql -u root -p
CREATE DATABASE grocery_shop;
EXIT;

# Create .env file
cp .env.example .env
# Edit .env with your MySQL password
```

### 5️⃣ Run Migrations
```bash
python manage.py migrate
```

### 6️⃣ Create Admin User
```bash
python manage.py createsuperuser
```

### 7️⃣ Start Server
```bash
python manage.py runserver
```

### 8️⃣ Access
- **Website**: http://127.0.0.1:8000/
- **Admin**: http://127.0.0.1:8000/admin/

## 📦 Download as ZIP

1. Go to: **https://github.com/MGShah/all-for-you-grocery**
2. Click green **"Code"** button
3. Click **"Download ZIP"**
4. Extract and follow steps above!

---

**Need detailed help?** See [SETUP_GUIDE.md](SETUP_GUIDE.md)