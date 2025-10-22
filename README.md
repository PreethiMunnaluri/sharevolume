# SEC Entity Shares Outstanding Viewer

This single-page responsive web application, built with HTML, Tailwind CSS, and JavaScript, allows users to view the maximum and minimum common stock shares outstanding for a specified company, based on data from the U.S. Securities and Exchange Commission (SEC) EDGAR API.

## Features

- **Dynamic Data Fetching:** Retrieves real-time company concept data from the SEC EDGAR API.
- **Max/Min Shares Outstanding:** Identifies and displays the highest and lowest reported common stock shares outstanding for a company since 2021.
- **Company Name Display:** Shows the official entity name from the SEC data.
- **Default Company:** Defaults to Baker Hughes (CIK: 0001701605).
- **Custom CIK Support:** Allows users to specify any 10-digit CIK (Central Index Key) in the URL to fetch data for other companies (e.g., `index.html?CIK=0001018724`).
- **Responsive Design:** Utilizes Tailwind CSS for a mobile-first, responsive user interface.

## How to Use

1.  **Open `index.html`:** Simply open the `index.html` file in your web browser. By default, it will display data for Baker Hughes.

2.  **View Data for Another Company:** To view data for a different company, append `?CIK=YOUR_CIK_NUMBER` to the URL.
    *   **Example for Apple Inc. (CIK: 0000320193):**
        `index.html?CIK=0000320193`
    *   **Example for Microsoft Corp (CIK: 0000789019):**
        `index.html?CIK=0000789019`

## Development Notes

### Data Source

Data is fetched from the SEC EDGAR API: `https://data.sec.gov/api/xbrl/companyconcept/CIK<CIK_NUMBER>/dei/EntityCommonStockSharesOutstanding.json`.

### Proxy for Cross-Origin Requests

When fetching data for CIKs other than the default Baker Hughes, the application uses a public CORS proxy (e.g., `https://api.allorigins.win/raw?url=`) to bypass Cross-Origin Resource Sharing (CORS) restrictions.

### SEC User-Agent Guidance

Per SEC guidance, requests to their API should include a descriptive `User-Agent` header. In a client-side web application, directly setting a custom `User-Agent` header for `fetch` requests to external domains is generally restricted by browsers. When using a proxy, the `User-Agent` of the browser is sent to the proxy, and it's the responsibility of the proxy to include an appropriate `User-Agent` when making its request to the SEC.

## Local Setup

No special setup is required. Just open `index.html` in your browser.

## Technologies Used

-   HTML5
-   Tailwind CSS (via CDN)
-   JavaScript (ES6+)
