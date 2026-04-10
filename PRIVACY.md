# Terminal Privacy Policy

_Last updated: April 10, 2026_

Terminal ("we", "us", "the app") is a mobile application that helps
travelers see real-time airport queue wait times, browse lounges, and
look up flight information. This policy explains what data we collect,
how we use it, and the choices you have.

## Plain-language summary

- We collect your **GPS coordinates** only while the app is open, and
  only to show your position on the map and detect which airport
  you're at.
- We **do not** collect your name, email, phone number, contacts,
  photos, calendar, or any other personally identifying information.
- Queue reports you submit (e.g. "I waited 10 minutes at Security
  T4") are uploaded **anonymously** and tagged with a random device
  ID generated on first launch. Wiping the app erases the ID.
- We use **Supabase** to store anonymous queue data, **MapLibre** and
  **OpenFreeMap** (OpenStreetMap tiles) to render the map, and
  **AirLabs** to look up flight information when you enter a flight
  number. No other third parties receive your data.
- If you subscribe to Pro, the purchase is handled by
  **Google Play Billing**. We never see your payment details.
- You can request deletion of any data tied to your device ID by
  emailing us (see below).

## What we collect

| Data | Purpose | Collected when | Stored where |
|------|---------|----------------|---------------|
| GPS coordinates | Show your position, detect airport, match slowdowns to queue zones | While the app is in the foreground | Not stored on our servers; used in-memory only |
| Queue reports (label + timestamps + GPS) | Crowd-sourced wait times for other travelers | When you label a detected slowdown | Supabase `reports` table, tagged with anonymous device ID |
| Feedback messages + ratings | Improve the app | When you submit via the Contribute tab | Supabase `feedback` table, tagged with anonymous device ID |
| Device ID (random UUID) | Attribute reports without identifying you | Generated on first launch | AsyncStorage (on your device) + Supabase |
| Flight number you type | Look up gate/terminal info | When you use the Flight tab | Sent to AirLabs API; not stored by us |
| Diagnostic info with feedback | Debug user-reported issues | When you submit feedback | Supabase `feedback.message` column (app version, platform, and the last 50 console log lines) |
| Notification preferences | Remember which alerts you want | When you toggle settings | AsyncStorage (on your device) |

We do **not** collect:

- Your name, email, phone number
- Contacts, calendar, photos, files
- Advertising identifiers (IDFA, AAID)
- Precise background location (we only access location while the app
  is in the foreground)
- Any cross-app tracking data

## How your data is used

- **GPS**: to render your position on the map, detect the airport
  you're at, and feed the queue-detection algorithm that fires the
  "What are you waiting for?" prompt. GPS is never transmitted to our
  servers on its own — only as part of a report you choose to submit.
- **Queue reports**: aggregated with reports from other travelers to
  estimate wait times at checkpoints. Other users see the aggregate;
  nobody sees your individual reports.
- **Feedback**: read by the development team to fix bugs and add
  features you ask for.
- **Diagnostic info** (attached to feedback): the app version,
  operating system, and recent app logs help us reproduce and fix
  issues you report.

## Third parties

We share the minimum necessary data with the following services:

- **Supabase** (database hosting) — stores anonymous queue reports,
  feedback, and zone data. <https://supabase.com/privacy>
- **MapLibre GL** (map rendering, open source) — renders the map
  locally on your device. No data is sent to MapLibre.
  <https://maplibre.org>
- **OpenFreeMap** (map tiles) — serves OpenStreetMap vector tiles to
  display the map. Your device requests tiles by geographic area;
  no personal data is transmitted. <https://openfreemap.org>
- **AirLabs** (flight data API) — receives the flight number you type
  to return gate and terminal info. <https://airlabs.co/terms>
- **RevenueCat** (subscription management, only if you buy Pro) —
  mediates the purchase via Google Play Billing. We never see card
  details. <https://www.revenuecat.com/privacy>
- **Google Play Billing** (payment processing, only if you buy Pro) —
  handles the transaction. <https://policies.google.com/privacy>

We do **not** sell your data, and we do not share it with advertisers.

## Your choices

- **Deny location**: the app still runs; you can manually browse
  airports and view queue data without contributing reports.
- **Deny notifications**: you can still use every feature; alerts
  won't fire.
- **Turn off data sharing**: in the Contribute tab, toggle "Share my
  position" off. We stop uploading any new reports from your device.
- **Delete your data**: email us your device ID (shown in the
  diagnostic info section of a feedback submission) and we will
  delete all rows associated with it within 30 days.
- **Uninstall**: wipes your device ID and all local preferences.

## Children's privacy

Terminal is not directed at children under 13. We do not knowingly
collect data from children. If you believe we have, contact us and
we will delete it.

## International users

Data is stored on Supabase infrastructure in the United States. If
you're using the app from the EU/EEA, UK, or another region with
GDPR-equivalent laws, you have the right to access, correct, or
delete your data. Email us your device ID with the request.

## Security

We use HTTPS for all network requests. Supabase enforces row-level
security on every table. Device IDs are opaque random strings, not
tied to any real-world identifier.

## Changes to this policy

If we make material changes, we will update the "Last updated" date
and, for significant changes, show a notice inside the app on next
launch.

## Contact

Questions, data deletion requests, or concerns:

**Email:** lulakcostudios@gmail.com
**Mail:** Terminal Queue App
