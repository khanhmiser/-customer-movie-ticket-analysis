# Online Movie Ticket Booking Data Analysis (2019–2022)

## Introduction

This project analyzes **customer online movie ticket booking behavior** during **2019–2022**.  
As a **Data Analyst** on the product development team at **Kompany**, the goal of the project is to provide actionable **insights** [...]

## System Architecture

The project directory structure is as follows:

```
project/
├── images/                          # Stores images, charts, and analysis visualizations
├── movie_ticket_data/               # Raw data directory
│   ├── campaign.csv                 # Marketing/promotion campaign data
│   ├── customer.csv                 # Customer data (ID, gender, year of birth)
│   ├── device_detail.csv            # Device data used for booking (model, platform)
│   ├── status_detail.csv            # Transaction status (ID, description, error group)
│   └── ticket_history.csv           # Booking transaction history (payment details, movie, promotions...)
├── notebooks/                       # Analysis notebooks, tests, processing and visualization
│   └── file analyst.ipynb           # Main notebook: load, process, clean & visualize data
└── README.md                        # Project description & instructions
```

## Objectives

- Understand customer behavior for online movie ticket booking over the past four years.  
- Provide **specific recommendations** to improve user experience and booking success rates.

## Problem definition

**Who (Target audience):**  
- **Internal:** Departments directly related to the booking process (Customer Service, Sales).  
- **External:** Who are the customers?  
  • Location: in Vietnam / abroad; region (urban, rural, province).  
  • Customer profile level: new customers, returning customers, verified-account customers.  
  • Demographics: gender, age, marital status, education (if available).

**What to analyze:**  
- Booking behavior through **website** and **mobile app**.

**When:**  
- Popular booking times: **year, month, day, hour, holidays, weekends, new movie releases**.

**Which factors:**  
What elements do customers typically interact with during online booking?
- Product: movie tickets.
- Booking device: website & app.
- Payment methods: various payment sources (in-app wallet, linked banks).
- Gifts, promotions, campaigns.

**How:**  
- Analyze customer experience, retention rates, step-level funnel performance.

## Analysis process

1. **Load Data:** Load and inspect raw data.  
2. **Data Cleaning:** Handle data types, nulls, duplicates, and join related tables.  
3. **Analyze:**  
   - Build **customer profiles** (age, gender).  
   - Analyze **booking trends over time** (month, week, hour).  
   - Evaluate **factors affecting purchase and payment behavior** (platform, device, method, promotions, movie type).  
   - Analyze **customer value and behavior**, **cohort retention**, and **payment success rates**.  
4. **Visualization & Insights:** Visualize data, extract trends, and recommend actions.

## Dataset information

- **Source:** Online movie ticket booking system.  
- **Time range:** 2019–2022  
- **Format:** `.csv`  
- **Total:** 5 data tables

### 1️ `customer.csv` — Customer information
| Attribute | Description |
|-------------|-------------|
| `customer_ID` | Unique identifier for each customer. |
| `usergender` | Customer gender. |
| `dob` | Customer year of birth. |

---

### 2️ `ticket_history.csv` — Booking history
| Attribute | Description |
|-------------|-------------|
| `ticket_id` | Unique booking ID for each transaction. |
| `customer_id` | Customer ID who made the transaction. |
| `paying_method` | Payment method used (e.g., **money in app**, **bank account**, **debit card**). |
| `theater_name` | Code or name of the theater complex where the booking was made. |
| `device_number` | Device ID used for booking, linked to `device_detail.csv`. |
| `original_price` | Original ticket price before applying promotions (unit: VND). |
| `discount_value` | Discount or promotion value applied. |
| `final_price` | Actual amount the customer paid after discount. |
| `time` | Booking timestamp (format: hh:mm:ss). |
| `status_id` | Transaction status ID, linked to `status_detail.csv` (e.g., success, failure, system error). |
| `campaign_id` | Marketing campaign ID applied to the booking (linked to `campaign.csv`). |
| `movie_name` | Name of the movie booked. |

---

### 3️ `device_detail.csv` — Device information
| Attribute | Description |
|-------------|-------------|
| `device_number` | Unique device identifier. |
| `model` | Specific device name or code. |
| `platform` | Platform or channel used to book — includes **mobile** (mobile devices) and **website** (web browser). |

---

### 4️ `campaign.csv` — Marketing campaigns
| Attribute | Description |
|-------------|-------------|
| `campaign_id` | Promotion campaign ID. |
| `campaign_type` | Type of marketing campaign. |

---

### 5️ `status_detail.csv` — Transaction status
| Attribute | Description |
|-------------|-------------|
| `status_id` | Transaction status identifier. |
| `description` | Detailed description of the status or error that occurred during payment. |
| `error_group` | Main error group, categorized by origin: **customer** (customer-side error), **external** (bank or third-party error), and **internal** [...].

## Tools and libraries used

- **Language:** Python  
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, `datetime`  
- **Tool:** Jupyter Notebook  
- **Version control:** GitHub

## Key findings

- **75% of customers** are aged **26–35**, a group with stable income and regular entertainment habits.  
- **Two peak seasons** for bookings occur in **May–July** (summer) and **October–December** (year-end releases).  
- **Weekend sales** are **1.5 times** higher than on weekdays (Monday–Thursday).  
- **89% of customers** book via the **mobile app**, of which **55% use iOS**.  
- Most customers come from **promotional campaigns**, however **the repeat rate is low**, mostly only booking **once**.

## Report
| **Online movie ticket booking behavior analysis (2019–2022)** | Detailed report in PDF format | [View Report](https://drive.google.com/file/d/1otfwKdD6RAmi8OEXXZN9hLMmzyoGo0Mo/view?usp=shar[...] )

Thank you for taking the time to review my project!  
If you are interested, want to collaborate on projects, or have job opportunities that fit, I am always open to discussing them.
