FIELDVAL — PROPERTY INSPECTION PROTOTYPE

FILES
- index.html: app structure
- style.css: responsive styling
- app.js: inspection forms, local storage, geolocation, photo log, CSV import/export, comparable-rate calculation and report draft
- service-worker.js: caches the app shell for offline reopening
- manifest.json: installable web app metadata

RUN IT
1. Put all files in the same folder.
2. Serve the folder from localhost or an HTTPS host (service workers and geolocation generally do not work from a plain file:// URL).
   Easy local option if Python is installed: run `python -m http.server 8000` inside the folder.
3. Open http://localhost:8000 in your browser, grant location/camera/file permissions when prompted, and optionally install it from the browser menu.
4. Open the app once online so the service worker can cache the app shell.

IMPORTANT LIMITATIONS
- This is a prototype, not a certified surveying, valuation, legal, or property due-diligence system.
- Inspection records and photo data are stored in this browser's localStorage. Export backups regularly. Large photos may exceed browser storage limits; images over 4 MB are skipped.
- Geotags and timestamps are recorded alongside each photo, not embedded into EXIF. Browser GPS can be unavailable or inaccurate, and browser metadata does not prove authenticity or prevent fraud.
- The app does not automatically retrieve historical sale transactions. Import a trusted CSV or enter comparables manually. CSV expected columns include address, price, area, distance_km, date, type. Imported distances are supplied by the user; the app does not calculate radius from coordinates.
- The valuation generator uses a simple median price-per-square-metre method plus user-entered adjustments. It is not a professional valuation model and must be reviewed by a qualified valuer.
- Before production use, replace localStorage with a robust IndexedDB/offline-sync architecture, encrypt sensitive data as appropriate, implement authenticated roles/audit logs, validate geospatial and transaction data, add conflict resolution, and obtain legal/privacy and professional review.
