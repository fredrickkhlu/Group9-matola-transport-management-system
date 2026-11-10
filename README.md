# MATOLA – Transport Management System UI
Responsive multi-page frontend prototype inspired by the supplied MATOLA screenshot.

## Included pages
- index.html – Homepage / Transit Radar
- find-transport.html – Search and available transport
- transport-details.html – Driver, vehicle and journey details
- login.html and register.html – Authentication interfaces
- passenger-dashboard.html – Passenger overview
- my-bookings.html – Passenger booking history
- messages.html – Message inbox preview
- profile.html – User profile
- driver-dashboard.html – Driver overview
- manage-vehicles.html – Vehicle management
- manage-routes.html – Route and transport listing form
- booking-requests.html – Driver booking requests
- about.html and contact.html – Information pages

## Run
Extract the ZIP and open `index.html` in a browser. Alternatively, open the folder in VS Code and run it with Live Server.

## Project stage
This is a static frontend prototype using HTML and CSS only. Forms, login, registration, bookings, messaging and dashboard actions are visual placeholders. No JavaScript, PHP, database or payment integration is included at this stage.


## Refinements
- Preserved MATOLA's navy, white and blue visual identity.
- Added a consistent inline SVG icon treatment for navigation.
- Added logout links to dashboard navigation and the shared profile page.
- Added a logout confirmation page returning to login.
- Shared messages and profile pages remain shared to avoid duplicate pages.
- Improved responsive navigation and keyboard focus states.

## Logout limitation
This is a static HTML/CSS prototype. The logout link returns to the login page, but true session destruction must be implemented in PHP when backend authentication is added.


## Local MATOLA service area
The prototype's sample locations now reflect the places supplied by the project team:
- Pama BIN
- Pa Shop wise
- Kwa 4K
- Kwa Jiga
- Kwa Chigaga
- Pa MOTA
- Ku MABUTU
- Ku GIRLS COMPLEX
- BOYS COMPLEX
- Ku Zero Budget
- Kwa Mlenga
- Mzuzu Town
- University of Livingstonia – Rumphi Campus

The example routes are interface placeholders, not verified transport services. Confirm exact routes, fare amounts, pickup points and departure times with local drivers before publishing live listings.


## Correct local journey model (University of Livingstonia, Rumphi)
MATOLA separates campus collection points from town/destination points.

### Campus pickup and drop-off points
- Kwa 4K
- Kwa Jiga
- Kwa Chigaga
- Pa MOTA
- Ku MABUTU
- Ku GIRLS COMPLEX
- BOYS COMPLEX
- Ku Zero Budget
- Kwa Mlenga

### Town / destination points
- Rumphi District
- Mzuzu Town
- Pama BIN
- Pa Shop wise

### Student travel pattern supplied by the group
- Outbound: vehicles collect students from the listed campus points and travel to Mzuzu.
- Typical outbound departure: around 6:00 AM.
- Expected Mzuzu arrival: around 10:00–11:00 AM.
- Return: students meet vehicles at Pama BIN in Mzuzu, then are dropped at their selected campus points.
- Vehicle examples: Toyota Sienta and Toyota Voxy.
- Fare guide: MWK 30,000–35,000 with bags.

These timings and fares are the group's supplied local service information, not a live timetable or guaranteed price. Driver listings must confirm the actual departure, available seats, baggage space and fare. Sample driver names and pictures in the UI are fictional placeholders.

## Image assets
Place the MATOLA logo and approved driver/vehicle photographs in `assets/images/`.
See `assets/images/README.txt` for filenames and replacement instructions. Current generated images are placeholders only.



## HTML and CSS only account flow
- `register.html` uses a native HTML form and sends the visitor to `account-created.html`.
- `account-created.html` displays an account-created message and uses an HTML meta refresh to open `login.html` after four seconds. A manual login link is also provided.
- `login.html` uses a native HTML form and navigates to `index.html` when submitted.
- No JavaScript authentication files are included.

## Important limitation
HTML and CSS alone cannot save user accounts, compare passwords, authenticate users, remember login status or protect private pages. In this static demonstration, registration and login are page-navigation demonstrations only. The browser's required-field and email-format checks are not account verification. Real authentication, role-based dashboards and secure logout require a server-side backend such as PHP and MySQL.


## Final navigation and mobile behaviour (HTML/CSS-only)
This static prototype uses two explicit navigation states because HTML/CSS cannot detect whether a visitor has authenticated:
- Public pages (`index.html`, `find-transport.html`, `about.html`, `contact.html`, `login.html`, `register.html`) show Log in and Get started. Their mobile navigation shows Home, Find and Log in only. It does not expose Messages or Profile.
- After the demo login form is submitted, it opens `home-logged-in.html`. This signed-in homepage and the dashboard/account pages show a single clearly visible Log out action instead of Log in/Get started.
- Signed-in mobile navigation shows Home, Messages, Profile and Log out. Logout is highlighted in red and also remains visible in the top mobile header.
- `logout.html` shows a signed-out confirmation with buttons to the public homepage and back to login.

Important: because this is HTML/CSS only, the two navigation states are separate static page versions. It cannot verify a password, remember a session, or prevent a visitor from typing a private page URL. Those functions require server-side PHP authentication and access checks.


### User experience rules applied
- Public visitors see only public navigation: Home, Find Transport, About Us, Contact, Log in and Get started.
- Public mobile bottom navigation contains Home, Find and Log in. It does not show Messages or Profile.
- Public transport cards use a login link for message actions.
- Signed-in page templates replace Log in/Get started with a high-contrast Log out action in the desktop/mobile header.
- Signed-in mobile navigation contains Home, Messages, Profile and Log out.
- Log out is styled in a clear red treatment and has a consistent icon and text label.


## Review fixes (latest version)
- Repaired the corrupted search form on `index.html` and `home-logged-in.html` (single clean From / To / Date form).
- Added the missing `viewport` and `description` meta tags on `login.html` and `register.html`.
- Fixed the duplicated fare text (`30,000–30,000–35,000`) in dashboards and bookings.
- Signed-in navigation is consistent: Home always opens `home-logged-in.html`; the active tab (desktop and mobile) now follows the current page, with `aria-current="page"`.
- `home-logged-in.html` now has a "Your workspace" section linking to the passenger and driver dashboards, and no longer shows public "Create account"/"Register" links.
- Logout page copy and buttons now agree with each other and with this README.
- Form labels are linked to their inputs (`for`/`id`) and fields have `name` attributes so a PHP backend can read them. Login and registration fields intentionally have no `name` yet, because they use `method="get"` and would otherwise put passwords in the URL.
- Replaced "MATOLA verified drivers" with neutral wording (sample drivers are not verified).
- Added skip-to-content link, favicon and theme colour.
- Pretty-printed the HTML, moved repeated inline styles into CSS classes and removed dead/duplicate CSS.

## Before adding the backend
- Use PHP sessions with a role check (passenger / driver) at the top of every private page.
- Switch login/register to `method="post"`, add `name` attributes to their fields and hash passwords with `password_hash()`.
- Add admin verification before a new "Driver" account can publish listings.
- Replace the placeholder contact details (`support@matola.example`, `+265 (0) 000 000 000`).
- Move the repeated header/footer/nav into PHP `include` files.
