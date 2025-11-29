# UI / UX & Planning Document

## 1. Goals

- Provide a **clean**, **simple**, and **responsive** interface for pharmacy staff.
- Ensure that both Admin and Pharmacist can quickly find the pages they need.
- Reduce the number of clicks required to perform frequent actions (add order, search medicine, view inventory).

## 2. Information Architecture

### Public Area

- Landing Page (`index.html`)
  - Brief introduction to the system.
  - Buttons/links to **Admin Login** and **Pharmacist Login**.

### Admin Area

- **Admin Dashboard**
  - Cards summarising:
    - Total medicines
    - Total companies
    - Total orders
    - Sales summary (today, last 7 days, etc.)
- **Companies**
  - Add Company
  - View Company list (with Edit/Delete options).
- **Medicines**
  - Add Medicine
  - View Medicine (with filters and actions).
- **Pharmacists**
  - Add Pharmacist
  - View Pharmacist list
- **Reports**
  - Sales Report (date range)
  - Stock Report
  - Pharmacist Report
- **Profile / Settings**
  - Change password
- **Logout**

### Pharmacist Area

- **Dashboard**
  - Sales summary for:
    - Today
    - Yesterday
    - Last 7 days
- **Search Medicine**
  - Search bar + filters (e.g., medicine name/company).
  - Add selected medicine to cart.
- **Cart**
  - Shows selected items with quantity and price.
  - Ability to remove items before placing the order.
- **Inventory**
  - Read-only inventory view.
- **Orders / Reports**
  - View all orders created by this pharmacist.
  - Invoice view per order.
- **Profile**
  - View/update own profile info.
  - Change Password.
- **Logout**

## 3. Layout & Visual Design

- Uses Bootstrap grid (`container`, `row`, `col-*`) to ensure responsiveness.
- Reusable layout structures:
  - Page header with title
  - Action buttons on the top-right (e.g., "Add Medicine")
  - Content area (tables, forms, cards)
- Typography:
  - **Poppins** font (via Google Fonts).
  - Headings (e.g., `<h1>`, `<h2>`) for section titles.
  - Body text (`<p>`, `<span>`) with comfortable line-height.
- Spacing:
  - Adequate `margin` and `padding` between sections.
  - Table rows with enough height for readability.
- Feedback:
  - Success, warning, and error messages displayed using Django's messages framework and Bootstrap alerts.

## 4. Navigation Flow (Wireframe-level Description)

1. **User lands on Home Page**
   - Sees navbar with links to "Home", "Admin Login", "Pharmacist Login".
2. **Admin logs in**
   - Redirected to Admin Dashboard.
   - From sidebar/top-nav, admin can access:
     - Dashboard
     - Companies
     - Medicines
     - Pharmacists
     - Reports
     - Logout
3. **Pharmacist logs in**
   - Redirected to Pharmacist Dashboard.
   - From navigation, pharmacist can access:
     - Dashboard
     - Search Medicine
     - Cart
     - Inventory
     - Orders / Reports
     - Profile
     - Logout

## 5. Future Enhancements 

- Dark mode toggle.
- Pagination + advanced filters on inventory tables.
- AJAX-based search for medicines.
- Export reports as CSV or PDF.