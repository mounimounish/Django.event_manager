# Event Manager — Online Event Booking & Catering System

[![Django](https://img.shields.io/badge/Django-5.2%20%7C%206.0-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

A modern, full-featured Django web application designed for comprehensive event management, slot reservations, and dynamic catering customization. **Event Manager** provides a seamless, professional booking experience for clients while streamlining event scheduling, venue showcase, interactive menu personalization, and automated cost calculation.

---

## 🌟 Key Features

### 1. User Authentication & Profiles (`accounts`)
* **Secure Registration & Login**: Multi-field registration with user credentials, personal contact information, address details, and avatar upload.
* **reCAPTCHA Protection**: Google reCAPTCHA integration on registration to prevent bot submissions.
* **User Dashboard**: Dedicated profile view displaying account information, verified membership status, and profile picture.
* **Profile Management**: Inline profile updates supporting image uploads and contact changes.

### 2. Event Showcase & Venue Galleries (`events`)
* **Featured Packages Catalog**: Browse curated event packages with base rates, package descriptions, and visual covers.
* **Detailed Event Overview**: Comprehensive package specifications with direct booking and enquiry options.
* **Venue Media Showcase**: Dedicated photo galleries for inspecting **Indoor Banquet Spaces** and **Outdoor Lawns**.

### 3. End-to-End Booking Workflow
* **Slot Booking**: Select and reserve event dates and time slots with venue preview access.
* **Interactive Catering Selection**:
  * Dynamic toggle to include or skip multi-course dining.
  * Side-by-side comparison of **Vegetarian** and **Non-Vegetarian** menus with per-head pricing.
* **Menu Customizer**:
  * Customize included dishes by removing unwanted items.
  * Pick replacement dishes from the available extra menu pool.
* **Event Logistics & Hospitality Configuration**:
  * Guest capacity and headcount estimation.
  * Dynamic menu tier selection linked to chosen dietary preferences.
  * Service crew and supplier headcount.
  * Custom celebration cake orders (kg).
  * Hospitality add-ons: Welcome Drinks, Welcome Chaats, and Royal Paan counter.

### 4. Transparent Cost Calculation & Invoicing
* **Itemized Quotation**: Real-time breakdown of base package, dining subtotal, cake, suppliers, maintenance, post-event cleaning, and GST (6%).
* **Grand Total Verification**: Review all specifications before finalizing the reservation.
* **Automated Email Receipts**: Branded booking confirmation emails dispatched via SMTP with full booking details.

### 5. Clean, Human-Made UI/UX
* **Modern & Clean Aesthetic**: Crisp white cards, high-contrast typography, and intuitive form controls.
* **Full-Bleed Media Sections**: Rich hero banners with background photography and dark gradient overlays.
* **Mobile-Responsive**: Fully responsive navigation with mobile collapsible menu and adaptive grid layouts.

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Backend Framework** | [Django 5.2 / 6.0](https://www.djangoproject.com/) |
| **Language** | [Python 3.10+](https://www.python.org/) |
| **Frontend** | HTML5, Vanilla CSS3, [Bootstrap 5.3](https://getbootstrap.com/) |
| **Icons & Typography** | [Bootstrap Icons](https://icons.getbootstrap.com/), Google Fonts (*Outfit* & *Plus Jakarta Sans*) |
| **Database** | MySQL (with SQLite compatibility) |
| **Security & Verification** | [django-recaptcha](https://pypi.org/project/django-recaptcha/) |
| **Image Processing** | [Pillow](https://pypi.org/project/Pillow/) |
| **Email Backend** | Django SMTP Email Backend (TLS/SSL) |

---

## 📁 Project Directory Structure

```plaintext
Django.event_manager/
│
├── accounts/               # User authentication, profile management & forms
│   ├── forms.py            # User registration, profile & update forms
│   ├── models.py           # Extended userDetails model with address & avatar
│   ├── views.py            # Login, registration, home, profile & update controllers
│   └── urls.py             # Account URL patterns
│
├── events/                 # Event catalog, slot booking, catering & invoicing
│   ├── forms.py            # EnquiryForm
│   ├── models.py           # EventsList, EventType, indoor/outdoor images, menus, FinalDetails
│   ├── views.py            # Slot booking, catering selection, customizer, price calculator
│   ├── utils.py            # Helper utilities for cost computation
│   └── urls.py             # Event management URL patterns
│
├── btrpy/                  # Core project configuration
│   ├── settings.py         # Django settings, DB config, static/media, email credentials
│   ├── urls.py             # Global URL routing
│   └── wsgi.py             # WSGI application entry
│
├── static/                 # Static assets
│   ├── CSS/style.css       # Modern, responsive design system & theme tokens
│   └── images/             # Backgrounds, badges, and default placeholders
│
├── templates/              # HTML templates
│   ├── base.html           # Master layout with responsive navbar & modern footer
│   ├── home.html           # Hero section & event package catalog
│   ├── login.html          # Authentication login card
│   ├── registration.html   # Multi-column registration card with reCAPTCHA
│   ├── userprofile.html    # Profile dashboard with avatar & address details
│   ├── update.html         # Profile edit form
│   └── events/             # Booking flow & catering templates
│       ├── slotbooking.html            # Date and time slot booking
│       ├── next.html                   # Catering menu options (Veg / Non-Veg)
│       ├── customize.html              # Interactive dish replacement customizer
│       ├── final_details.html          # Headcount, add-ons & logistics form
│       ├── confirmation.html           # Booking verification summary
│       ├── final_price.html            # Itemized cost breakdown & invoice
│       ├── success.html                # Booking confirmation screen
│       ├── eventsDescription.html      # Event package overview
│       ├── indoorimages.html           # Indoor venue photo gallery
│       ├── outdoorimages.html          # Outdoor space photo gallery
│       ├── enquire.html                # Event enquiry form
│       ├── enquiry_thanks.html         # Enquiry thank-you confirmation
│       └── confirm_email_template.html # Branded HTML email receipt
│
├── media/                  # User uploads (profile pictures, event covers, venue galleries)
├── manage.py               # Django management utility
└── README.md               # Project documentation
```

---

## 🚀 Quick Start & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/mounimounish/Django.event_manager.git
cd Django.event_manager
```

### 2. Set Up Virtual Environment
```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install django pillow django-recaptcha mysqlclient python-dotenv
```
*(Note: If using MySQL on Windows without pre-compiled binaries, you can also use `pip install pymysql`.)*

### 4. Configure Environment Variables
Create a `.env` file in the root directory:
```env
DB_NAME=btrpy_db
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_HOST=127.0.0.1
DB_PORT=3306
```

### 5. Run Database Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Start the Development Server
```bash
python manage.py runserver
```

Visit the application in your browser at:
```
http://127.0.0.1:8000/
```

---

## 📸 Application Workflow

1. **Browse Events (`/home`)**: Discover packages with transparent base pricing and rich cover photos.
2. **Select & Schedule (`/events/slotbooking/<id>/`)**: Choose your event date and start time.
3. **Catering Customization (`/events/next/` & `/events/custmoize/`)**: Select Veg or Non-Veg tiers and customize dishes.
4. **Final Details (`/events/final/`)**: Enter guest headcount, staff requirements, cake sizes, and hospitality add-ons.
5. **Invoice & Order Confirmation (`/events/calculate_price/`)**: Review itemized charges, GST, and confirm booking.
6. **Confirmation & Email Dispatch**: Receive an automated email receipt with the finalized booking summary.

---

## 👨‍💻 Author

Developed with care by **[Mounish](https://github.com/mounimounish)**.

Feel free to star ⭐ the repository if you found this project helpful!
