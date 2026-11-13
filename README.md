# Neosis — Interactive Demo

A clickable, front-end-only demo of **Neosis**, an internal image-data toolkit used by an image-recognition (IR) team to manage detection models, test images and product packshots.

Everything runs in one HTML file, with no server, no build step and no network calls. All data is sample data.

> **Not the production app.** This is a portfolio mockup of the real tool's UI and workflows. It contains no company data, credentials or backend code.

## Run it

1. Open `neosis-demo.html` in any modern browser (Chrome, Edge, Firefox, Safari).
2. On the login page, enter any valid email (for example `demo.admin@example.com`) and click **Continue**. The Google and Microsoft buttons also sign you in. Nothing is sent anywhere.

It works offline and can be hosted as a static file. The file is about 11 MB because the sample images are embedded in it.

## What you can try

Use the **User / Admin** switch in the header to see both views. Admin sees edit actions and the Control Panel. User is read-only.

| Area | What it shows |
|---|---|
| **Login** | Email sign-in plus simulated Google and Microsoft options. |
| **Dashboard (home)** | Tool cards grouped as Core Workflows and Utilities, plus a header search that finds tools. |
| **Model Dashboard** | Per-company model versions (.pt, nano .onnx and class files) for SKU, Asset, Rack and Object models. Includes version history, accuracy and remarks, a **Retraining required** flag for models under 97%, "Not present" rows for missing models, and search and tenant filters. Admin can edit accuracy and remarks, edit company names, hide and restore companies and files, and use the Deleted section. |
| **Testing Images** | Brand picker, then a gallery per brand. Filter by asset, open a full-page preview with previous and next, and download. Admin can select and delete, and the upload buttons are simulated. |
| **Packshots** | Brand picker, then a packshot grid with an **Annotation Name / Name** toggle and the same full-page preview. |
| **Control Panel** (Admin only) | IR members with domain validation, tenants with a write-only masked connection string and a Test connection step, and Force sync with per-tenant status. Deleting a tenant moves its companies to Deleted. |
| **Not in demo** | Pseudo Labelling, Image Extraction and Accuracy Report appear as disabled cards, because they need internal company data. |
| **Themes and layout** | Light and dark themes, responsive down to phone width, keyboard-accessible dialogs. |

## Simulated behaviour

- Edits, deletes, hides and sign-in live in memory only and reset when you reload the page.
- Uploads, logo changes and ZIP downloads are disabled and show a message.
- **Test connection** succeeds for any text. Include the word "bad" to see a failed test.
- Nothing you type is stored or sent anywhere.

## Sample data and privacy

- **Model data:** the models, accuracy history and remarks come from a dummy JSON dataset. Company ids are made up. Dates are shifted so the latest sync appears recent.
- **Images:** sample photos and packshots are used for illustration. Metadata (EXIF, GPS) was stripped, burned-in coordinates, addresses and timestamps were cropped out, and photos with identifiable people and stock or watermarked images were removed.
- **Packshot names:** L'Oréal packshot names are generic placeholders. Brand names and logos belong to their owners and are shown for illustration only.
- **Emails:** all emails use `example.com` and similar domains.

## Tech

- Vanilla HTML, CSS and JavaScript in a single file, with a hash router.
- Fonts (Plus Jakarta Sans), images, logos and data are embedded in the file.
- Images are compressed to WebP: testing images up to 1280px, packshots up to 800px.
- No frameworks, no external requests.

The real Neosis uses a FastAPI backend with a React front end. None of that is included here.
