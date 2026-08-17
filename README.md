# Table-Reservation-System
# InfoSys 22 – Assignment 1

A Django-based backend application for managing restaurant table reservations.

This project implements the required backend components for the assignment:

- `models.py`
- `forms.py`
- `views.py`
- `urls.py`
- `migrations/`

# Features

The system provides backend functionality for:

- Customer management
- Table category management
- Restaurant table management
- Reservation status management
- Reservation management
- Payment management
- Reservation filtering
- Reservation audit logging

# Reservation Validation

The system validates that:

- The number of guests is greater than zero.
- The reservation end time is later than the start time.
- The number of guests does not exceed the selected table's capacity.

---

# Models

The application contains seven main models:

1. **Customer** – Stores customer information.
2. **TableCategory** – Defines restaurant table categories.
3. **Table** – Stores individual reservable tables.
4. **ReservationStatus** – Stores reservation status values.
5. **Reservation** – Records table reservations.
6. **Payment** – Records payments associated with reservations.
7. **AuditLog** – Records important actions performed on reservations.

---

## Forms

The following Django ModelForms are implemented:

- `CustomerForm`
- `TableCategoryForm`
- `TableForm`
- `ReservationStatusForm`
- `ReservationForm`
- `PaymentForm`

The forms include appropriate labels, widgets, and validation.

---

## API Endpoints

### Customers

```text
GET/POST  /customers/
POST      /customers/add/
GET       /customers/<id>/
POST      /customers/<id>/edit/
POST/DELETE /customers/<id>/delete/
```

### Table Categories

```text
GET/POST  /table-categories/
POST      /table-categories/add/
GET       /table-categories/<id>/
POST      /table-categories/<id>/edit/
POST/DELETE /table-categories/<id>/delete/
```

### Tables

```text
GET/POST  /tables/
POST      /tables/add/
GET       /tables/<id>/
POST      /tables/<id>/edit/
POST/DELETE /tables/<id>/delete/
```

### Reservation Statuses

```text
GET/POST  /reservation-statuses/
POST      /reservation-statuses/add/
POST      /reservation-statuses/<id>/edit/
POST/DELETE /reservation-statuses/<id>/delete/
```

### Reservations

```text
GET/POST  /reservations/
POST      /reservations/add/
GET       /reservations/<id>/
POST      /reservations/<id>/edit/
POST      /reservations/<id>/cancel/
POST/DELETE /reservations/<id>/delete/
```

Reservation filtering:

```text
/reservations/?customer=<customer_id>
/reservations/?reservation_date=<YYYY-MM-DD>
```

### Payments

```text
GET       /payments/
POST      /payments/add/
GET       /payments/<id>/
POST      /payments/<id>/edit/
GET       /reservations/<reservation_id>/payments/
```

### Audit Logs

```text
GET       /audit-logs/
GET       /audit-logs/<id>/
```

Filter audit logs by reservation:

```text
/audit-logs/?reservation=<reservation_id>
```

### Django Admin

```text
/admin/
```

---

## Project Structure

```text
table_reservation_system/
│
├── manage.py
│
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
└── reservation_app/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── forms.py
    ├── models.py
    ├── urls.py
    ├── views.py
    ├── migrations/
    │   └── ...
    └── tests.py
```

`__pycache__/` may also appear automatically because Python generates it while running the application.

---

## Installation and Setup

### 1. Create/activate the virtual environment

Windows:

```bash
venv\Scripts\activate
```

### 2. Install Django

```bash
pip install django
```

### 3. Apply migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 4. Check the project

```bash
python manage.py check
```

Expected result:

```text
System check identified no issues (0 silenced).
```

### 5. Run the development server

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/
```

The project root returns the Table Reservation System API information.

---

## Django Admin

To view and manage database records through Django Admin, create a superuser:

```bash
python manage.py createsuperuser
```

Then run:

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/admin/
```

---

## Testing the API

The API endpoints can be accessed through a browser or an API testing tool such as Postman.

Example:

```text
http://127.0.0.1:8000/customers/
```

Other main endpoints:

```text
http://127.0.0.1:8000/table-categories/
http://127.0.0.1:8000/tables/
http://127.0.0.1:8000/reservations/
http://127.0.0.1:8000/payments/
http://127.0.0.1:8000/audit-logs/
```

---

## Migration Verification

To view migration status:

```bash
python manage.py showmigrations
```

Applied migrations should be marked with `[X]`.

The project should also pass:

```bash
python manage.py check
```

without errors.

---

## Assignment Scope

This project follows the required backend scope for InfoSys 22 Assignment #1:

**ERD → Models → Forms → Views → URLs**

The assignment does not require:

- HTML templates
- CSS
- JavaScript
- Bootstrap/Tailwind
- Frontend layout
- Visual design
- Deployment
