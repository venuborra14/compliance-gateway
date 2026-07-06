# PORTGUARD — Corridor Compliance Gateway
### Demo One-Pager · EU-India-ASEAN Customs Shield

**Live demo:** https://venuborra14.github.io/compliance-gateway/

---

## What Is This?

PORTGUARD is an interactive prototype of a **freight forwarder compliance gateway** — the system a freight forwarder uses to validate a shipment's documentation before it is transmitted to customs authorities.

The demo simulates a real-world scenario: an Indian exporter is preparing a shipment to either the EU (Rotterdam / Hamburg) or ASEAN (Kuala Lumpur / Singapore). Before the forwarder hits "transmit," PORTGUARD runs the documentation through four live customs compliance checks and surfaces every issue that would cause a border hold, tariff rejection, or manual query — in real time, as fields are edited.

The output is a **MLETR-compliant signed electronic payload** — a cryptographically sealed transferable document ready for direct submission to customs AS2 endpoints. No paper, no manual re-keying.

---

## The Problem It Solves

Cross-border trade documentation errors are expensive:
- A name mismatch between the IEC register and the commercial invoice triggers a manual officer query at Nhava Sheva — days of delay.
- A 4-digit HS code instead of the required 8-digit ITC-HS code causes an automatic border hold under ICEGATE 2.0.
- Missing EUDR geolocation polygon data for coffee or rubber shipments results in port loading denial under EU deforestation regulation.
- Regional Value Content below 35% on an ASEAN shipment voids the preferential AITIGA tariff — the importer pays full duty.

PORTGUARD catches all of these before submission.

---

## The Four Customs Systems

| System | Jurisdiction | What It Validates |
|--------|-------------|-------------------|
| **ICEGATE 2.0** | India | Company name match between IEC register and commercial invoice; 8-digit ITC-HS classification code |
| **ICS2** | European Union | Pre-loading advance cargo manifest; positive gross weight declared; CBAM carbon emissions ID for steel |
| **EUDR** | European Union | Geolocation polygon of production plot uploaded to EU Information System (mandatory for coffee and rubber) |
| **AITIGA** | ASEAN | Regional Value Content (RVC) ≥ 35% for preferential tariff under the ASEAN-India Trade in Goods Agreement |

---

## How the Demo Works

### Layout

The screen is split into two panels:

**Left — Documentation Desk**
The forwarder's data entry form. Enter company names, commodity type, HS code, cargo weight, and corridor-specific fields (EUDR toggle, CBAM ID for EU; FOB value and VNM for ASEAN). Every field change immediately re-evaluates all compliance rules — there is no submit button.

**Right — Status Room**
- **Global Health Score** — a circular gauge showing the overall compliance index (0–100%). Red = critical block, amber = subjective risk, green = ready to transmit.
- **FIATA Liability HUD** — auto-calculates maximum carrier liability in USD using the FIATA Model Rules formula: Weight (KG) × 2 SDR × 1.33.
- **Live Risk Alerts** — every active finding displayed as a card with severity badge (CRITICAL or WARN), affected system, and a one-click AUTO-RESOLVE button.
- **Passed Checks Strip** — green chips confirming every rule that has been satisfied.
- **Transmit Console** — generates and displays the full MLETR-signed JSON payload with cryptographic seal tags and signature hash.

### Route Toggle

Switch between **Route A (EU corridor)** and **Route B (ASEAN corridor)** using the segmented control in the header. The form adapts — EUDR and CBAM fields appear for Route A; RVC (Regional Value Content) fields appear for Route B.

---

## Pre-Set Demo Scenarios

Three one-click scenarios are available in the bottom-left panel for a rapid demonstration:

### Scenario 1 — Non-Compliant Coffee Export to Germany
Loads a coffee shipment with a 4-digit HS code and no EUDR geolocation polygon. Triggers two CRITICAL findings and drops the score to ~40%.

**Use this to show:** How quickly documentation errors escalate and what the forwarder faces at the port if they don't catch it in advance.

### Scenario 2 — Failed AITIGA Rubber Sourcing to Malaysia
Switches to Route B (ASEAN) with rubber at RVC 20% — well below the 35% AITIGA threshold. Triggers a CRITICAL finding that voids the preferential tariff.

**Use this to show:** The ASEAN Rules of Origin check and the financial consequence of incorrect sourcing declarations.

### Scenario 3 — Fully Compliant Export (Green State)
Loads a clean cotton shipment on Route A with all fields correct: names match, 8-digit HS code, EUDR toggled on, CBAM ID present. Score is 100%, gauge is green, payload is ready to transmit.

**Use this to show:** What the end state looks like and then generate the signed payload to demonstrate the MLETR output.

---

## Recommended Demo Flow

1. **Open Scenario 1** → show two critical alerts and a red gauge (~1 min)
2. **Click AUTO-RESOLVE** on each alert → watch the score climb to 100% in real time (~1 min)
3. **Click "Generate Signed Payload"** → walk through the terminal animation and the JSON output (~1 min)
4. **Switch to Route B**, load **Scenario 2** → show the AITIGA RVC failure and auto-fix (~1 min)
5. **Edit a field manually** (e.g. change the weight) → show the FIATA liability number updating live (~30 sec)

Total: ~5 minutes end-to-end.

---

## Key Concepts to Highlight

**Real-time validation** — every keystroke re-runs all four compliance rule engines. There is no network call; the logic runs entirely in the browser, making it instant and offline-capable.

**Auto-resolve** — the system doesn't just flag problems; it knows the correct remediation for each finding and can apply it in one click. This demonstrates the gateway's ability to act as an intelligent co-pilot, not just a validator.

**MLETR compliance** — the generated payload is structured as an electronic transferable record under the UNCITRAL Model Law on Electronic Transferable Records. It includes a DID (Decentralised Identifier) for the issuer, an electronic seal tag, and an RSA-2048 signature hash — the building blocks of paperless trade.

**Corridor-aware logic** — the same forwarder interface handles two fundamentally different regulatory regimes (EU and ASEAN) by switching rule sets at runtime. This reflects the multi-corridor reality of Indian export logistics.

**FIATA liability** — the automatic calculation of maximum carrier liability from declared cargo weight gives the forwarder an instant risk figure before they commit to the shipment.

---

## What This Is Not

This is a **prototype and demonstration tool**. It uses synthetic data only. No real customs systems are contacted, no actual filings are submitted, and no real RSA keys are used. All compliance rules are simplified approximations of live regulatory requirements for illustration purposes.

---

*PORTGUARD · Demo build · Synthetic data only · v2.4.1*
