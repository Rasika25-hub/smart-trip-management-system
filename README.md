# SmartTrip – Intelligent Travel Planning and Management System(TMS)

A web-based travel planning and trip management application that brings destination discovery, budget-aware booking, day-wise itinerary planning, weather information, and trip administration into one place.

The project is designed to make trip planning more organized for travellers while giving administrators and tour guides tools to manage bookings and trip-related information.

## Highlights

- **Destination discovery** — browse available destinations and view destination details.
- **Trip planning and booking** — select trip dates, duration, passenger and transport details, and review trip costs.
- **Day-by-day itineraries** — generate an itinerary preview before booking and view the itinerary associated with a booking.
- **Weather-aware planning** — retrieve forecast information from the [Open-Meteo API](https://open-meteo.com/) and use it to support travel planning.
- **Multiple user roles** — separate traveller, administrator, and tour-guide workflows.
- **Booking lifecycle management** — view bookings, handle cancellation flows, and track booking/payment status.
- **Payment and receipt flow** — includes an application-level payment workflow and receipt generation. This should be treated as a demonstration flow unless a real payment gateway is explicitly configured.
- **Reviews and feedback** — collect trip feedback and provide administration views for reviewing it.
- **Admin dashboard** — manage destinations, bookings, guides, hotels, and feedback; view booking-related summary information.
- **Relational data model** — stores users, destinations, places, bookings, guides, hotels, payments, and feedback in a database.

## What makes it useful
scm-history-item:c%3A%5CUsers%5Crrras%5COneDrive%5CDesktop%5CProjects%5CIntelligent-Climate-Pattern-Risk-Prediction-Using-Data-Mining?%7B%22repositoryId%22%3A%22scm0%22%2C%22historyItemId%22%3A%22bc478c2c0c6f2e5defec64043c818d3136757dea%22%2C%22historyItemDisplayId%22%3A%22bc478c2%22%7D
Rather than focusing only on destination listings, TMS connects the main stages of a trip workflow: **discover → plan → estimate → book → view itinerary → provide feedback**. Weather information and itinerary previews help travellers consider practical trip details before confirming a booking, while role-based pages support day-to-day administration.

## Technology Stack

| Area | Technology |
|---|---|
| Main web application | Python, Flask |
| Front end | HTML, CSS, Jinja templates |
| Database | SQLite |
| Weather data | Open-Meteo API |
| Security utilities | Werkzeug password-hashing utilities and Flask sessions |
| Additional files in repository | PHP pages and a MySQL schema for a PHP/Laragon implementation |

> **Repository note:** The project currently contains both a Flask/SQLite implementation (`app.py`) and PHP/MySQL files. The run instructions below describe the Flask application, which is the entry point associated with `requirements.txt`. The PHP files may require separate configuration and should not be assumed to run as part of the Flask app.

## Getting Started (Windows)

### Prerequisites

- Python 3.10 or later (a recent supported Python 3 version is recommended)
- Git (optional, for cloning the repository)
- Internet access for live weather data

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

Alternatively, download the repository as a ZIP file and extract it.

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure application secrets

Before sharing or deploying the project, update the Flask application so its secret key is read from an environment variable rather than hard-coded in `app.py`. Do not commit real secret keys, passwords, or API credentials.

For local development, set a unique secret key in your terminal before starting the app. The code must be configured to read that environment variable for it to take effect.

### 5. Start the application

From the project root directory:

```bash
python app.py
```

Open the local address printed by Flask in your browser (commonly `http://127.0.0.1:5000`).

The application uses `database/trip_management.db` and `database/schema_sqlite.sql`. If you want a clean setup, back up any existing database and follow the database initialization logic in `app.py` before removing or replacing database files.

## Main User Workflows

### Traveller
1. Register or log in.
2. Browse destinations and review destination details.
3. Preview an itinerary and enter trip details.
4. Proceed through the booking and payment demonstration flow.
5. View bookings, receipts, and itineraries.
6. Submit feedback for a trip where supported.

### Tour guide
- View assigned trip information.
- Access guide trip pages and respond to or update trip status where available.

### Administrator
- Review dashboard summaries.
- Manage destinations, bookings, guides, and hotels.
- Review traveller feedback and other booking-related information.

Available actions depend on the current implementation and database configuration.

## Project Structure

```text
TMS/
├── app.py                       # Flask application entry point
├── requirements.txt             # Python dependencies
├── database/
│   ├── schema_sqlite.sql        # SQLite schema and seed data
│   ├── schema.sql               # MySQL schema for the PHP implementation
│   └── trip_management.db       # Local SQLite database (review before publishing)
├── templates/                   # Jinja HTML templates for Flask
├── static/                      # Static assets
├── admin/                       # PHP administration pages
├── includes/                    # PHP shared files, including DB connection
└── *.php                        # Additional PHP/MySQL pages
```

## Data and Integration Notes

- Weather information depends on network access and the availability of the Open-Meteo service. If the API is unavailable, weather-based features may not return live information.
- The payment workflow is intended for demonstration unless a verified payment provider integration is added.
- Sample records and database contents may be used for local testing. Replace demo data before using the application with real users.
- Do not use this project with real personal, payment, or credential data until authentication, authorization, validation, secret management, and deployment security have been reviewed.

## Security Checklist Before Making the Repository Public

- [ ] Remove hard-coded secrets and database passwords from source files.
- [ ] Load secrets from environment variables and keep local `.env` files out of Git.
- [ ] Review `database/trip_management.db` for personal information, test accounts, and sensitive records.
- [ ] Remove Python cache files and other generated files from version control.
- [ ] Change all demo credentials and avoid publishing real user data.
- [ ] Test role-based access and booking/payment flows before deployment.

## Current Scope and Future Improvements

Potential next steps include consolidating the Flask and PHP implementations, adding automated tests, improving configuration management, documenting database migrations, integrating a real payment gateway, and preparing a secure production deployment.

## Learning Outcomes

This project demonstrates practical application development across web routing, templating, database operations, user roles, booking workflows, external API consumption, and CRUD-based administration.

## License

No license has been specified yet. Add a license file if you want to define how others may use, modify, or distribute this project.
