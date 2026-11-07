# WholesalePro — Wholesale Business Management (v1.0)

A local-first web application for managing a single wholesale business. It includes customer and supplier records, products and stock adjustments, batch expiry tracking, quotations, GST-oriented sales invoices, payment tracking, purchases, expenses, reports, WhatsApp message sharing and JSON backups.

## Run the app

### Option A — Open directly

1. Extract the project ZIP.
2. Open `index.html` in a modern browser (Chrome, Edge or Firefox).
3. Start adding your business details in **Settings → Business profile**.

The app uses browser `localStorage`, so no database installation is needed for this starter version. For more reliable local browser storage, run the included `START-WINDOWS.bat` file (Windows with Python installed), then open `http://localhost:8000`. You can also run `python -m http.server 8000` from this folder.

### Option B — Run with Vite

Install Node.js, open a terminal in this folder, then run:

```bash
npm install
npm run dev
```

Open the local URL printed by Vite (normally `http://localhost:5173`). To create a static production bundle:

```bash
npm run build
```

The output will be in `dist/`.

## Included features

- Dashboard with monthly invoiced sales, expenses, customer count and outstanding balances.
- Customer records with phone, WhatsApp, GSTIN, state, address, credit period and messaging consent flag.
- Supplier records.
- Product catalogue with SKU, HSN, unit, purchase/selling price, GST rate and configurable stock thresholds.
- Plus/minus stock adjustments with a stock movement ledger.
- Batch records and expiry alerts for perishable goods.
- Quotations with multiple line items and conversion into invoices.
- GST-oriented tax invoice print layout with CGST/SGST or IGST calculation based on the business and customer states.
- Partial and full payment tracking.
- Purchase receiving that increases stock.
- Operating expense entry and reporting.
- CSV exports and full JSON backup/restore.
- WhatsApp click-to-chat with a prefilled message.

## Important limitations of this starter build

This is a **single-browser prototype / MVP**, not yet a hosted multi-user accounting system.

- Data is stored in the browser on the device where it is entered. It does not sync between computers, staff accounts or mobile devices. Export JSON backups regularly.
- WhatsApp opens a chat with a prepared message. It does not automatically attach or send the invoice PDF. Print/save the document as PDF and attach it manually in WhatsApp. Automatic document delivery requires the official WhatsApp Business Platform and a backend.
- The invoice is a GST-oriented template and calculator, not a certified GST filing or e-invoicing product. Verify HSN codes, rates, place of supply, mandatory particulars, numbering and applicability with a qualified GST professional before issuing live invoices. E-invoice IRN, e-way bill and GST return filing integrations are not included.
- Purchase entry records received cost and stock, but a full purchase GST input-credit workflow is not included.
- No authentication, role permissions, cloud database, automated backups, audit-grade immutability or server-side validation is included yet.
- The initial code assumes products' entered unit prices follow the selected GST-inclusive/exclusive setting. Check this setting before creating documents.

## Suggested production upgrade

For real multi-user operations, move data to PostgreSQL (for example, Supabase or a managed PostgreSQL service), add server-side authentication and role permissions, audit logs, scheduled backups, hosted PDF storage, and the official WhatsApp Business Platform. Add GST API integrations only after confirming the business's registration and compliance requirements.

## Files

- `index.html` — application shell
- `styles.css` — responsive UI styling
- `app.js` — application logic and local data layer
- `package.json` — optional Vite development/build scripts

## Deploy to Netlify

### Recommended: GitHub + Netlify (automatic updates)

1. Extract the ZIP file on your computer.
2. Open the extracted `wholesalepro` folder. The files `index.html`, `app.js`, `styles.css`, `package.json`, and `netlify.toml` should be directly inside it.
3. Create a new GitHub repository and upload the *contents* of this folder to the repository root (avoid creating an extra nested `wholesalepro/wholesalepro` folder).
4. In Netlify, choose **Add new project → Import an existing project**, connect GitHub, and select that repository.
5. Netlify should read `netlify.toml`. Confirm these settings if asked:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Deploy the site. Future pushes to the connected GitHub branch will trigger new deployments.

### Manual deployment

For a manual deploy, run these commands from the `wholesalepro` folder on your computer:

```bash
npm install
npm run build
```

Then upload the generated `dist` folder to Netlify's manual deploy area. The manual deploy area expects the built output folder, not the source folder.

### Important data and production note

Netlify hosts the static website files; it does not turn this browser-local prototype into a shared cloud application. Business records are stored in `localStorage` in each browser/device and are not synchronised. Before using this for live business records or several staff/devices, add a secure cloud database, authentication, server-side validation, access rules and automated backups. Test a backup/restore before entering real records. Do not publish live customer or financial data in a public Git repository.
