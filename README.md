# Paginated Web Scraping

This file includes a Python script for scraping images from paginated web pages using Selenium. It navigates through pages of a website that uses pagination to organize content, ensuring that images from each page are captured and saved locally.

## Features

- Automatically navigates through paginated content to access multiple pages.
- Filters images by their extensions, supporting `.jpg`, `.jpeg`, `.png`.
- Downloads and saves images to a specified local directory, creating unique filenames for each according to date and time format.

## Prerequisites

Before running this script, ensure you have the following installed:

- Python 3.6 or higher
- Selenium WebDriver
- ChromeDriver (or another driver compatible with your browser of choice)

## Setup

1. Clone this repository to your local machine.
2. Install the required Python packages:
