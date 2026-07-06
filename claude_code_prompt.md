SYSTEM INSTRUCTIONS FOR CLAUDE CODE: BUILD PORT CORRIDOR COMPLIANCE INTERACTIVE DEMO

Build a highly polished, premium, and fully interactive single-file HTML dashboard that showcases a "Compliance-First" Trade Gateway for the EU-India-ASEAN trade corridors.

The application must be completely self-contained in a single index.html file, utilize Tailwind CSS (via CDN) for styling, and include highly interactive vanilla JavaScript logic to simulate real-world customs validation checks.

1. DESIGN SYSTEM & VISUAL GUIDELINES

Theme & Palette: Neutral-dark premium developer aesthetic.

Backgrounds: Deep slates and charcoal (bg-slate-950, bg-slate-900, bg-slate-900/50)

Borders: Sophisticated subtle borders (border-slate-800/80)

Typography: Clean, high-contrast text (text-slate-100, text-slate-400, text-slate-500)

Interactive Accents:

PASSED / SAFE: Cyber Emerald (#10b981 / text-emerald-400 / bg-emerald-500/10)

SUBJECTIVE RISK / WARNINGS: Amber Gold (#f59e0b / text-amber-400 / bg-amber-500/10)

CRITICAL BLOCKS / REJECTIONS: Intense Crimson (#ef4444 / text-red-400 / bg-red-500/10)

Font: Inter or similar clean system sans-serif. Use monospace (font-mono) for simulated terminal outputs and raw JSON data fields.

Vector Icons: Import Lucide Icons via CDN (https://unpkg.com/lucide@latest) to provide crisp, dynamic SVG visual aids next to state statuses and navigation controls.

2. APP LAYOUT STRUCTURE (Split-Screen Interface)

The dashboard must feature a responsive, split-screen layout (12-column grid on desktop, stacking vertically on mobile):

A. Sleek Header

Branding: "PORTGUARD // EU-India-ASEAN Customs Shield".

Route Segmented Toggle: A premium physical toggle to instantly switch between:

Route A: India ──> European Union (Rotterdam/Hamburg)

Route B: India ──> ASEAN (Kuala Lumpur/Singapore)

Selecting a route must instantly transition the entire application's data state, input fields, warning engines, and risk scores.

B. Left Panel: Interactive Documentation Desk (Shipment Profile)

A form representing what the forwarder's clerk sees, dynamically updating as fields are altered:

Company Profile Validation:

IEC Registration Name: Text Input (Default: "Ganesha Textiles Pvt Ltd")

Invoice Legal Name: Text Input (Default: "Ganesha Textiles Limited")

Status Flag: A tiny helper label showing whether these names match exactly or pose a subjective string-matching risk to Indian customs officers.

Commodity & Classification:

Commodity Dropdown: Selection between Coffee Beans, Organic Cotton Yarn, Structural Steel Plates, and Natural Rubber Sheeting.

HS Code Input: Text field (Default: "5208"). If user types fewer than 8 digits, a warning fires.

Gross Cargo Weight (KG): Number field (Default: 12500).

Dynamic Value & Tariff Fields (Visible only for Route B - ASEAN):

FOB Value (USD): Number field (Default: 15000).

VNM (Value of Non-Originating Materials) (USD): Number field (Default: 9500).

Environmental / ESG Compliance Fields (Visible only for Route A - EU):

EUDR Plot Coordinates: A toggle switch for "Polygon Geolocation Uploaded" (Default: false).

CBAM Carbon Emissions ID: Text Input (Default: "EU-CBAM-90812-CN").

C. Right Panel: Live Compliance Status Room & API Sandbox

This is the "magic" section that closes the deal. It must update instantly when left-hand side values change.

Global Health Score Ring:

A beautiful SVG circular gauge displaying a dynamic score from 0% to 100%.

A status pill changing color based on score: "CRITICAL BLOCK" (Red, 0-59%), "SUBJECTIVE RISK" (Amber, 60-89%), or "READY TO TRANSMIT" (Green, 90-100%).

Customs Shield (Live Risk Alert Terminal):

A running stack of cards displaying active compliance errors. Each card must show the specific target system (ICEGATE, ICS2, AITIGA, EUDR) and have an "AUTO-RESOLVE" button that fixes the form input automatically with one click.

Dynamic Liability HUD:

A small calculation HUD illustrating liability protection under the FIATA Model Rules. It must evaluate the formula:


$$\text{Liability Cap (USD)} = \text{Gross Weight (KG)} \times 2 \text{ SDR} \times 1.33$$


(Displaying the real-time weight value multiplied by $2 \text{ SDR} \times 1.33 = 2.66$).

The "Transmit to Customs" Console:

A simulated terminal container.

A CTA button: "Generate Signed Payload (MLETR-Compliant)".

When clicked, triggers a loading animation that prints a beautifully formatted, colorized JSON payload incorporating secure electronic signature fields, dynamic e-seal tags, and digital title-transfer hashes.

3. INTERACTIVE COMPLIANCE LOGIC & RULES ENGINE

The JavaScript code must run reactive checks on user inputs without needing a page refresh:

Name Mismatch Rule (ICEGATE / Indian Customs):
If "IEC Registration Name" does not exactly match "Invoice Legal Name" (e.g., "Pvt Ltd" vs "Limited"), fire an Amber Warning:

"Subjective Rejection Risk: String mismatch between IEC register and commercial invoice. Local assessment officer will query/reject at Nhava Sheva/Chennai."

8-Digit HS Code Rule (ICEGATE 2.0):
If "HS Code" length is less than 8 characters, fire a Red Critical Rejection:

"ICEGATE 2.0 Error: India mandates an 8-Digit ITC-HS classification code. 4 or 6-digit codes trigger instant manual queries and border holds."

AITIGA Rules of Origin (ASEAN Route only):
Calculate RVC dynamically using the formula:


$$RVC = \left(\frac{\text{FOB} - \text{VNM}}{\text{FOB}}\right) \times 100$$


If the calculated $RVC < 35\%$, fire a Red Critical Rejection:

"AITIGA Rule Failure: Regional Value Content is [Calculated RVC]%, falling below the mandatory 35% threshold. Preferential tariff will be rejected by ASEAN customs."

EUDR Geolocation Gate (EU Route with Coffee/Rubber only):
If Route is EU, and Commodity is Coffee Beans or Natural Rubber Sheeting, and "EUDR Plot Coordinates" is toggled Off, fire a Red Critical Rejection:

"EUDR Enforcement Block: Geolocation polygon coordinates missing. Cargo will be denied loading at Nhava Sheva port."

Pre-Set Demo Mock Scenarios:
Provide quick-clickable text links/buttons at the bottom of the form to auto-fill the form with specific states:

"Scenario 1: Non-Compliant Coffee Export to Germany" (loads errors for HS, EUDR geolocation).

"Scenario 2: Failed AITIGA Rubber Sourcing to Malaysia" (loads low RVC % failure).

"Scenario 3: Fully Compliant Export State (Green)" (loads perfectly matching names, 8-digit HS, passed RVC, and toggled ESG indicators).

Ensure all HTML structures, Tailwind styles, SVG rings, and script blocks are written clearly inside a single index.html file.