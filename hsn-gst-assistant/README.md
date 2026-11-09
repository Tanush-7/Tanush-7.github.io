# HSN & GST Rate Verification Assistant

Decode an HSN code, reach the right official source, and keep a worksheet of the rates you verified yourself.

- **Problem source**: a developer unable to find a reliable HSN-to-GST-rate source with current conditional slabs: [r/developersIndia thread](https://www.reddit.com/r/developersIndia/comments/1xr9v2a/).
- **Features**: HSN structure breakdown (chapter/heading/sub-heading/tariff), standard chapter titles, links to the official GST portal Search HSN service, the CBIC Tax Information Portal notifications, and the master rate notification No. 09/2025-Central Tax (Rate) dated 17.09.2025 (effective 22.09.2025), plus a verification worksheet (code, description, rate you verified, notification no., condition, date) with localStorage and CSV export.
- **Run it**: open `index.html` in a browser, or use the GitHub Pages site.
- **Limits**: deliberately asserts no rates - GST rates are conditional and change by notification, so each rate must be verified for the specific product and date. Not tax advice.
