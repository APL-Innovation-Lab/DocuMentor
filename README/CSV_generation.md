# Resolving Drupal Events CSV Download Issue

## Overview

This document outlines the troubleshooting and resolution process for an issue encountered while attempting to download a CSV file of events from the Drupal website of the Austin Public Library. The initial request resulted in a 503 error, leading to a series of steps to identify and remedy the problem.

## Steps Taken

### 1. Identifying the Issue

- Initially, accessing the URL for downloading the events CSV returned a 503 error, indicating server unavailability.

### 2. Testing the URL

- Attempted to access the URL directly and through various methods to confirm the issue was consistent.

### 3. Switching the Method of CSV Generation

- Investigated the Drupal Views UI, identifying the method used for CSV generation.
- Switched from Data Export to REST export in the Views UI, based on recent findings that this method is more reliable.

### 4. Adding a Dummy Parameter

- Added a dummy parameter to the URL to bypass potential caching issues, which did not resolve the issue.

### 5. Utilizing the Development Server

- Moved the test to a development server to isolate the problem from production environment factors.

### 6. Encountering and Overcoming Protocol Security Issues

- Encountered security warnings due to the use of HTTP; however, switching to HTTPS was not feasible in the development environment.

### 7. Effective Use of `curl` for Download

- Utilized the `curl` command line tool to bypass browser and network security limitations, successfully downloading the CSV.

## Conclusion and Recommendations

- **Changing the CSV Generation Method:** Utilizing REST export in Drupal's Views UI proved more reliable than Data Export for generating CSV files.
- **Command Line as a Powerful Tool:** The `curl` command line tool can be a fast and effective method for downloading files, bypassing common browser and network issues.
- **Simplicity of Command Line:** Using `curl` is straightforward, making it accessible for users across different operating systems, including Windows and macOS.

### Command for Downloading CSV

```plaintext
curl "https://library.austintexas.gov/library_events_a.csv?date1=2024-01-01&date2=2024-03-31&dummy=12345" -o "library_events.csv"
```

This experience highlights the importance of flexibility in troubleshooting and the effectiveness of command line tools for navigating and resolving web service issues.
