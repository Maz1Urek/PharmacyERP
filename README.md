# Pharmacy Management Web Application

## 1. Problem Understanding & Requirements

### Problem Statement
Small and medium-sized pharmacies often manage stock, billing, and daily sales manually (using registers or spreadsheets). This leads to:
- Difficulty in tracking **available medicines**
- Errors in **billing and stock updates**
- No quick view of **daily / weekly / monthly sales**
- No per-pharmacist performance tracking

This project provides a **web-based Pharmacy Management System** that allows:
- Admin to manage companies, medicines, pharmacists, and inventory
- Pharmacists to create orders, manage carts, and view their own dashboards and reports

### Target Users
- **Admin (Owner / Manager)** of the pharmacy  
- **Pharmacists / Staff** working at the pharmacy

### Mapping Features to Requirements
| Requirement                                      | Feature / Screen                                                       |
|-------------------------------------------------|------------------------------------------------------------------------|
| Maintain list of medicines and stock            | Add / View / Update / Delete Medicine, Inventory pages                |
| Maintain list of companies                      | Add / View Company                                                    |
| Pharmacist login & profile                      | Pharmacist Login, Profile page                                        |
| Quick overview of sales and orders              | Admin Dashboard, Pharmacist Dashboard                                 |
| Track orders and invoices                       | Order creation, Invoice generation, Order history                      |
| Analyse sales and stock                         | Sales report, Stock report, Pharmacist performance report             |
| Secure access                                   | Django-based authentication, role-based admin vs pharmacist dashboards|

---

## 2. Design (UI / UX & Planning)

### Page Flow

**Public**
- `/` → Landing page (`index.html`)
- `/admin_login/` → Admin login
- `/pharmacist_login/` → Pharmacist login

**Admin Flow**
- `admin_dashboard` → Summary of orders, sales, and inventory
- Manage Companies → Add / View / Delete company
- Manage Medicines → Add / View / Edit / Delete medicine
- Manage Pharmacists → Add / View pharmacists, reset password
- Reports
  - Sales report (date range)
  - Stock report
  - Pharmacist-wise report
- Logout

**Pharmacist Flow**
- `user_dashboard` → Today / yesterday / last 7 days sales summary
- Search Medicine → Add to cart
- Cart → Create order (invoice generated)
- View Inventory
- View own Sales Report
- View Orders (filters: today / yesterday / last 7 days)
- Profile & Change Password
- Logout

### UI / UX Notes

- Uses **Bootstrap** for grid layout and responsiveness.
- Common design elements:
  - Top navigation bar (admin & pharmacist versions)
  - Consistent color palette from the template
  - Cards / tables for displaying summary information
  - Mobile-friendly navigation using the Bootstrap navbar.
- Typography:
  - Base font-family from Google Fonts (`Poppins`).
  - Font weights used to create visual hierarchy (e.g., headings vs body).
- Navigation:
  - Clear menu items for Dashboard, Inventory, Reports, and Profile.
  - Breadcrumb-like headings on each page to clarify the current section.

---

## 3. Deployment

See `docs/deployment.md` for step-by-step instructions.  
The project is designed to run on:

- Localhost (development)
- PythonAnywhere / Render / Railway (any Django-compatible platform)

Key deployment characteristics:
- Uses **SQLite** by default (can be swapped with PostgreSQL/MySQL).
- Static files are served via Django staticfiles (collectstatic in production).
- Secret settings like `SECRET_KEY` should be placed in environment variables in production.

---

## 4. Implementation / Technical Correctness

- Backend: **Django** (Python)
- Frontend: HTML, **Bootstrap CSS**, basic JavaScript.
- Authentication: Django's built-in auth system.
- Database Models:
  - `Company`
  - `Medicine`
  - `Pharmacist`
  - `Cart`
  - `Order`
  - `History`
- Queries use the Django ORM with filters, aggregates, and annotations where required.
- Forms are defined using Django `forms.py` to validate data server-side.

Responsiveness:
- Most pages use Bootstrap's grid system (`container`, `row`, `col-*` classes),
  so pages adjust to different screen sizes.

Error Handling:
- Custom user-friendly `404.html` and `500.html` templates (see `templates/` directory).
- Django messages framework is used for success and error notifications
  (e.g., login failures, delete confirmations).

---

## 5. Functionality & Features

### Core Features
- Admin and Pharmacist login.
- Company management (CRUD).
- Medicine management (CRUD) with quantity and price.
- Pharmacist management.
- Cart and order creation by pharmacists.
- Invoice generation per order.
- Daily / custom-range sales and stock reports.

### Extra / Value-Added Features
- Dashboard cards summarising sales for today/yesterday/last 7 days.
- Pharmacist-wise performance report.
- Low-level error messages using Django `messages`.
- Date-range filters for admin reports.

---

## 6. Code Quality & Documentation

- Views and models include comments/docstrings explaining the purpose of each major function.
- Consistent naming conventions (`snake_case` for functions, `CamelCase` for models).
- Project-level documentation:
  - This `README.md`
  - `docs/ui_ux.md`
  - `docs/deployment.md`
  - `docs/viva_prep.md`

---

## 7. How to Run Locally

### Prerequisites
- Python 3.x
- pip
- virtualenv (recommended)

### Steps

```bash
cd Pharmacyproject
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt  # If not available, install Django manually: pip install django
python manage.py migrate
python manage.py createsuperuser  # for initial admin login
python manage.py runserver
```

Open `http://127.0.0.1:8000/` in your browser.

---

## 8. Viva / Oral Examination Preparation

See `docs/viva_prep.md` for a list of sample viva questions and short, clear answers
related to this project and general web development concepts.