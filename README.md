# Quickbase → WordPress Training Details Integration
*A reference implementation for displaying Quickbase Events in WordPress using Elementor Pro, ACF, and custom PHP/CSS.*

---

## Overview

This repository provides an example implementation for organizations that manage their event or training catalog in **Quickbase** but need to display that data on a **WordPress** website.

It demonstrates how to:

- Pull or map Quickbase Events data into WordPress  
- Use **Advanced Custom Fields (ACF)** to store field values  
- Build dynamic layouts using **Elementor Pro**  
- Render event information (date, time, trainers, cost, registration links, etc.) using **shortcodes and helper functions**  
- Apply optional styling with custom CSS  

This setup is designed to be **modular**, **extensible**, and easy for others to replicate or adapt.

---

## Project Structure

├── php/

│ └── quickbase-events-integration.php # Custom PHP integration functions & shortcodes

├── css/

│ └── quickbase-events.css # Styling for Event listings & detail pages

├── docs/

│ └── integration-overview.md # Written explanation of the full workflow

└── README.md


*(Your directories may differ depending on how you organize your repo. This is a suggested structure.)*

---

## Key Tools Used

### Quickbase
- Primary database for Events, Courses, and Trainers  
- Provides structured fields that map directly into WordPress  
- Supports formula fields for HTML cleanup, slugs, and conditional formatting  

### WordPress
- Public-facing website  
- Contains the Elementor templates, ACF fields, and theme-level PHP  

### Elementor Pro
- Controls event listing pages, Loop Grids, and Single Event templates  
- Dynamic Tags populate layout elements from ACF fields  

### Advanced Custom Fields (ACF)
- Stores incoming Quickbase data on WordPress posts/pages  
- Defines field groups like:  
  - Event Name  
  - Start/End Date & Time  
  - Trainers  
  - Registration Link  
  - Description (HTML-ready)  
  - Cost  
  - Status or Visibility flags

### Custom PHP

Located in `php/quickbase-events-integration.php`, this file provides:

- Helper functions for retrieving Quickbase field values  
- Shortcodes (e.g., `[arc_training_cost]`)  
- Formatter utilities for dates, trainers, descriptions, etc.  
- A pluggable pattern that others can extend  

### CSS

A small stylesheet (`quickbase-events.css`) enhances trainer cards, detail pages, spacing, and responsive behavior.

---

## How the Integration Works

### 1. Quickbase Holds the Master Data

Designated fields in a Quickbase Events table contain:

- Event title  
- Description (cleaned or HTML-friendly)  
- Start and end date/time  
- Trainer names  
- Registration URL  
- Cost  
- Flags such as “Show on Website”  

Formula fields may be added to pre-format HTML, generate slugs, or combine trainer names.

---

### 2. WordPress Uses ACF to Store Mirror Fields

A custom post type or dedicated page uses ACF fields to hold:

- `qb_event_id`  
- `event_title`  
- `event_start_time`  
- `event_end_time`  
- `event_trainers`  
- `event_cost`  
- `event_registration_url`  
- `event_description_html`  
- Additional metadata used in Elementor

---

### 3. Elementor Pro Builds the Public Templates

Two primary templates:

#### Events Listing Template
- Displays upcoming events  
- Uses filters, sorting, and ACF fields  
- Can be used in a Loop Grid or Archive page  

#### Single Event Template
- Event title & subtitle  
- Date/time  
- Trainer bios  
- Registration button  
- Cost and other metadata  
- Description rendered from Quickbase HTML  

---

### 4. PHP Functions Provide Shortcodes & Formatting

The included PHP defines functions such as:

- `arc_td_get_field_value()` – fetches a specific Quickbase field  
- `arc_td_sc_cost()` – outputs formatted cost through the `[arc_training_cost]` shortcode  

Additional helpers may format dates, trainers, badges, and icons.

You may place these functions in:

- A child theme’s `functions.php`  
**or**  
- A lightweight custom plugin  

---

### 5. Optional Styling with CSS

`quickbase-events.css` includes overrides for:

- Trainer cards  
- Description spacing  
- Clean list formatting  
- Responsive layout improvements  

---

## How to Use This Repository

### 1. Download the example files  
Clone the repo or download ZIP.

### 2. Copy PHP into your theme or plugin  
Add the functions from `quickbase-events-integration.php` into:

- `wp-content/themes/your-child-theme/functions.php`  
or  
- `wp-content/plugins/your-custom-plugin/plugin.php`

### 3. Create ACF Fields  
Match ACF fields to your needs or adjust the PHP mappings.

### 4. Build or Import Elementor Templates  
Create your own templates using Dynamic Tags, or import template JSON files if included.

### 5. Apply CSS  
Place the CSS file in your theme or paste it into Elementor Site Settings.

### 6. Connect Your Quickbase Workflow  
Use API pulls, scheduled syncs, or webhooks to populate event data.

Note: This repository focuses on **display and formatting patterns**, not enforcing a specific sync method.

---

## Screenshots & Examples (coming soon)

Planned additions:

- Example training detail page  
- Elementor layouts  
- Quickbase table field list  
- ACF field group screenshots  

---

## Who This Is For

- Quickbase builders wanting clean external display  
- WordPress/Elementor users needing structured event content  
- Developers implementing low-code or hybrid integrations  

If you manage events or training schedules in Quickbase and want them to appear beautifully and consistently on the web, this repo provides a strong starting point.

---

## License

MIT License – free to use, adapt, and extend.

---

## Contributions & Feedback

Suggestions, improvements, and questions are welcome!  
Open an issue or submit a pull request.

---

## Author

**Alan Lytle**  alytle@thearcoregon.org
Operations Support Director • The Arc Oregon

