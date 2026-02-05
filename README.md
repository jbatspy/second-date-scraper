# Second Date Scraper

A Python web scraper that automatically downloads all "Second Date Update" episodes from the Brooke and Jeffrey morning show website.

## Overview

This project scrapes the [Brooke and Jeffrey website](https://www.brookeandjeffrey.com/featured/second-date-bjitm/) to download all available Second Date Update episodes as MP3 files.

## How It Works

1. **Scrape Episode Links**: Uses Selenium to load the page, click "Load More" repeatedly, and collect all episode URLs
2. **Extract Embed URLs**: Parses each episode page to find the Omny.fm embed URL from the page's preloaded state
3. **Capture MP3 URLs**: Opens the Omny.fm player, simulates clicking play, and captures the MP3 URL from network traffic
4. **Download**: Downloads each MP3 with a sanitized filename based on the episode URL

## Requirements

- Python 3.11+
- Chrome browser
- ChromeDriver (compatible with your Chrome version)

## Installation

1. Clone or download this repository

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install selenium beautifulsoup4 requests
```

4. Install ChromeDriver:
   - Download from [ChromeDriver Downloads](https://chromedriver.chromium.org/)
   - Ensure it's in your PATH or specify the path in the code

## Usage

Open `second_date_scraper.ipynb` in Jupyter Notebook and run the cells in order:

1. **Cell 1**: Import dependencies
2. **Cell 2**: Scrape all episode links from the website
3. **Cell 3**: Download all episodes (main pipeline)
4. **Cell 4**: (Optional) Retry failed downloads

Downloaded episodes will be saved to the `second_date_episodes/` folder.

## Features

- **Auto-pagination**: Automatically clicks "Load More" until all episodes are loaded
- **Skip existing files**: Won't re-download episodes that already exist
- **Progress tracking**: Shows detailed progress for each download
- **Error handling**: Continues processing even if individual episodes fail
- **Filename sanitization**: Creates clean, readable filenames from episode URLs

## Tech Stack

- **Selenium**: Browser automation for dynamic content
- **BeautifulSoup**: HTML parsing
- **Requests**: HTTP requests and file downloads
- **Chrome DevTools Protocol**: Network traffic capture

## Project Structure

```
Brooke_And_Jeffrey_In_the_Morning/
├── second_date_scraper.ipynb    # Main scraping notebook
├── second_date_episodes/        # Downloaded MP3 files (excluded from git)
├── venv/                        # Virtual environment (excluded from git)
├── .python-version              # Python 3.11
├── .gitignore                   # Git ignore rules
└── README.md                    # This file
```

## Notes

- The scraper runs with headless Chrome by default
- Each episode takes ~18-28 seconds to process (due to wait times for page loads and play button simulation)
- Total download size: ~21 GB for 650+ episodes
- The `second_date_episodes/` folder is excluded from git due to large file sizes

## License

This project is for personal use only. All content belongs to Brooke and Jeffrey / iHeartRadio.
