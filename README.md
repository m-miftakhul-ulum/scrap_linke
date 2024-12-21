# LinkedIn Data Scraper and Google Sheets Integration

This project scrapes education-related data from LinkedIn profiles using Selenium and saves the results to a Google Sheets document. It supports headless browser operation and uses Google Sheets API for data storage.

## Features

- Scrapes data such as university, major, and year of education from LinkedIn profiles.
- Saves scraped data directly to a Google Sheets spreadsheet.
- Utilizes cookies to maintain session for LinkedIn login.
- Runs in headless mode to avoid displaying the browser during scraping.

## Prerequisites

1. Python 3.10+
2. Install the required libraries:

   ```bash
   pip install -r requirements.txt
   ```
3. Download the ChromeDriver binary compatible with your version of Google Chrome and add it to your system PATH.
4. Create a Google Cloud project and enable the Google Sheets API and Google Drive API.
5. Generate a service account JSON file and save its path in the `.env` file.

## Setup

1. **Environment Variables**:
   Create a `.env` file with the following variables:

   ```env
   SERVICE_ACCOUNT_FILE=path/to/your/service-account.json
   SPREADSHEET_ID=your-google-sheet-id
   ```

2. **Google Sheets Setup**:
   - Share the Google Sheet with the email address from your service account JSON file.
   - Replace `SPREADSHEET_ID` in the `.env` file with your Google Sheet's ID (found in the URL).

3. **Cookies**:
   - Login to LinkedIn in a browser, export cookies as JSON, and save them as `cookies.json` in the same directory.

## Usage

1. **Run the Script**:
   Execute the script with Python:

   ```bash
   python script.py
   ```

2. **Modify LinkedIn URLs**:
   Replace the `data` variable in the script with the LinkedIn profile URLs you want to scrape.

3. **View Results**:
   Scraped data will automatically be appended to your Google Sheets document.

## Code Breakdown

1. **Google Sheets Configuration**:
   The script authorizes access to Google Sheets using the service account credentials.

2. **Cookie Management**:
   The script loads `cookies.json` to maintain the LinkedIn session.

3. **Selenium WebDriver**:
   - Configured to run in headless mode for background operation.
   - Uses XPath to locate and extract education-related data from LinkedIn profiles.

4. **Error Handling**:
   Handles missing or inaccessible elements gracefully, defaulting to `"kosong"` for missing data.

5. **Data Saving**:
   Appends each row of scraped data to the specified Google Sheet.

## Important Notes

- **LinkedIn Scraping**: Scraping LinkedIn data may violate LinkedIn's terms of service. Use responsibly.
- **Headless Mode**: The browser runs in the background and doesn't open a visible window.
- **Rate Limiting**: To avoid being blocked by LinkedIn, consider implementing rate limiting or rotating proxies.

## Dependencies

- `selenium`: Automates the browser for scraping.
- `gspread`: Interacts with Google Sheets API.
- `google-auth`: Authenticates with Google APIs.
- `python-dotenv`: Loads environment variables from a `.env` file.

## Example Output

The following data is appended to Google Sheets:

| LinkedIn URL                          | University          | Major             | Year  |
|---------------------------------------|---------------------|-------------------|-------|
| https://www.linkedin.com/in/example1/ | Example University  | Computer Science  | 2022  |
| https://www.linkedin.com/in/example2/ | Another University  | Mechanical Eng.   | 2020  |

## License

This project is open source and available under the [MIT License](LICENSE).

## Disclaimer

This project is intended for educational purposes only. The author is not responsible for any misuse of the code.

