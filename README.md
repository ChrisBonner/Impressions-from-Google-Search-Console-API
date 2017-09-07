# Get Google Search Console Impression Data

## Description
This simple python script uses Google Search Console API to retrieve your website's Web, Image and Video impression data for a specific date range from Google Search Console. It will also create a directory based on the URL of the website and save the impression data in csv files in that directory. Which is really convenient if you have a lot of websites you need to track impression data for.

It will also create a error.log file to store any errors or log run information.

## Requirements
Enabled Search Console API - https://developers.google.com/webmaster-tools/search-console-api-original/v3/quickstart/quickstart-python

Website must be verified in your Google Search Console account and have impression data to pull

## installation
Download script and place it in the directory you want to store all your impression data in.
Copy & Paste in the webmasters.dat and client_secrets.json provided from Enabling Search Console API into the same directory.

## Instructions

You can run the script from command-line by navigating to the directory and typing in python gsc-impression-data.py URL Date Date

### URL
replace URL_of_website with the URL in your Search Console. The URL needs to be exact match. 
If your site uses https and has the leading www, you must enter https://www.example.com/
You must include trailing slash as well. 

### Date
The date format needs to be YYYY-MM-DD. I do not have checks for incorrect date format, but it will show in the log file if there are any.

**The first date** is the start date of the date range. It cannot exceed current date - 92 days. This is due to Google only storing data for 90 days plus the 2 day lag time for processing data.

**The second date** is the end date of the date range. It cannot be any soon than current date - 2 days, and in some cases current date - 3 days. This is because Google has a 2 day lag time to process data, and in the rare cases where - 2 does not work, it means your data has not populated by Google yet.

## Results
Once the script has successfully ran, navigate to the directory. Now you will find a error.log file, which stores errors and logs, a new directory with the URL naming, and inside that directory 3 CSV files. web-impressions.csv, image-impressions.csv and video-impressions.csv.

The data in the impression.csv are in the order of:
Date, Clicks, Impressions, CTR, Average Position
