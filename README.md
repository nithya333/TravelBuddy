# TravelBuddy: Automated Flight Price Comparator and Booking Assistant

[![Platform: UiPath Studio](https://img.shields.io/badge/RPA_Platform-UiPath_Studio-orange?style=flat-square&logo=uipath)](https://www.uipath.com/)

**TravelBuddy** is an enterprise-grade Robotic Process Automation (RPA) solution built using **UiPath Studio** to automate real-time flight fare collation, cross-portal data validation, and automated clinical travel reporting. By replacing manual, high-frequency, and repetitive cross-browser window navigation, the bot ingests user parameters, applies robust UI scraping configurations, detects the absolute cheapest booking target, and structuralizes data delivery end-to-end.

---

## Architectural Overview

The automation framework executes a highly modular, decoupled sequential sequence partitioned into distinct runtime execution workflows:


```

[ UiPath Assistant Client ] --> Ingests Origin, Destination, Travel Date & Email
|
v
[ Core RPA Engine Open Browser ] --> Establishes isolated target sessions
|
+-----------------------+-----------------------+
|                                               |
v                                               v
[ Portal A: MakeMyTrip ]                        [ Portal B: GoIbibo ]
* Dynamic Selector Entry                        * Dynamic Selector Entry
* AI Computer Vision Triggers                   * Dynamic Pop-up Suppression
* Character OCR Scraping Loop                   * Tabular Data Scraping Engine
|                                               |
+-----------------------+-----------------------+
|
v
[ Unified Data Table Object ]
|
v
[ Mathematical Price Minimizer ] --> Drops price to minimum threshold
|
v
[ Localized Data Storage Suite ] --> Writes master file (.xlsx)
|
v
[ SMTP/Outlook Email Engine ] ----> Pushes reporting logs to User Box

```

### 1. User Interface & Parameter Ingestion
* Deploys a user-friendly configuration client inside **UiPath Assistant**, gathering `From City`, `To City`, `Travel Date`, and target `Email ID` without exposing the underlying code canvas.

### 2. Resilient Intelligent Scraping Layer
* **Computer Vision (CV) Operations:** Integrates structural anchor mapping algorithms to instantly spot and eliminate unexpected structural login walls, micro-transaction banners, and modal checkout prompts.
* **OCR Text Recovery:** Provides screen scraping engines that interpret graphics-rendered target metrics (such as precise airline carriers or discount items) where raw DOM trees fail to expose standardized selectors.
* **Fuzzy & Dynamic Selectors:** Implements parameterized wildcard tags (`*`) to ensure execution continuity despite variable query strings or localized promotional UI adjustments.

### 3. Data Integration & Reporting Pipeline
* Formats individual web structures into native `DataTable` records, sorting data matrices dynamically to catch the cheapest entry.
* Leverages **Excel Activities** to automatically write complete extracted flight inventories (Carrier Name, Departure/Arrival Times, Duration, Fare, and Booking Redirect Links) into a structured workbook layout.
* Triggers an automated **Mail Notification Module** using SMTP configuration setups, delivering the optimized selection parameters alongside an attached copy of the analytical spreadsheet.

---

## Prerequisites & Environments

* **Operating System:** Windows 10/11 (Architecture supported by UiPath execution profiles)
* **Development Engine:** UiPath Studio (Community or Enterprise License)
* **Execution Interface:** UiPath Assistant
* **Target Web Application Clients:** Google Chrome or Microsoft Edge (with installed **UiPath Web Automation Extension**)
* **Data Stores:** Microsoft Excel (.xlsx installation runtime or compatible file manipulation modules)

---

## Installation & Workflow Setup

1. **Clone the Repository Space:**
   ```bash
   git clone [https://github.com/nithya333/TravelBuddy.git](https://github.com/nithya333/TravelBuddy.git)
   cd TravelBuddy

2. **Open the Project File:**
Launch **UiPath Studio** and select `Open Project`. Target the `project.json` file inside the root repository clone path to automatically import variable scopes, dependencies, and execution assets.
3. **Verify Dependencies Configuration:**
Ensure the project dependencies manager updates and installs the latest versions of:
* `UiPath.UIAutomation.Activities`
* `UiPath.Excel.Activities`
* `UiPath.Mail.Activities`
* `UiPath.ComputerVision.Activities`


4. **Configure Extension Hooks:**
Verify that your web browser has the official **UiPath Web Automation** extension turned on to allow for structural browser interaction.

---

## Running the Bot

1. Click **Run** or **Debug** inside the Main workflow canvas (`Main.xaml`), or trigger execution directly through the **UiPath Assistant** layout panel.
2. Provide your target travel logistics inside the popup interaction windows (e.g., *From: Bengaluru, To: Mumbai, Date: DD-MM-YYYY*).
3. Ensure no manual interaction occurs while the automation takes control of your browser. The bot will open target aggregators, execute search functions, sort pricing sheets, format reports, and cleanly close out the open threads.

---

## Sample Output

<img width="559" height="719" alt="image" src="https://github.com/user-attachments/assets/501a0493-0f36-40ff-b98f-ecde5561399c" />

---

## System Advantages

* **Time Efficiency:** Reduces multi-portal flight tracking and comparative lookups from 15 minutes of manual browsing down to a sub-two-minute autonomous process.
* **Accuracy Assurance:** Eliminates human mapping mistakes, typo inputs, or missed price exceptions across hundreds of continuous rows.
* **Scalable Framework:** Designed modularly, enabling seamless extensions to parse additional transport verticals like luxury buses, bullet trains, or hotel bookings.
