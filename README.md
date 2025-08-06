# wikidata-stats
A simple command-line tool to automate the reporting of monthly contributions on Wikidata. This script fetches contribution data for a given period and calculates both the number of new pages created by the user and the number of unique, pre-existing pages edited by the user.

## **Features**

* **Calculates Statistics**: Reports on two mutually exclusive contribution types:  
  * **Created**: The number of new pages (items) created.  
  * **Edited**: The number of unique, pre-existing pages edited.  
* **Flexible Date Ranges**: Get stats for a specific month or a custom date range.  
* **User-friendly**: Prompts for your username and date preferences. No coding required to use.  
* **Saves Report**: Automatically saves the results to a .txt file for your records.  
* **Portable**: Can be run on any system with Python. Includes a helper script for easy execution on Windows.

## **Prerequisites**

Before you begin, ensure you have the following installed:

1. **Python 3**: This script is written in Python. You can download it from [python.org](https://www.python.org/downloads/).  
2. **Requests Library**: A Python library for making web requests. You can install it by running the following command in your terminal or command prompt:

```
pip install requests
```

## **How to Use**

1. Download the project files and place them in a folder on your computer. The expected file structure is:

```
wikidata-stats/
├── script/
│   └── wikidata_stats.py
└── run_stats.bat
```

2. Run the script using the method appropriate for your operating system.

### 

### **For Windows Users (Recommended)**

Simply double-click the run\_stats.bat file located in the main wikidata-stats folder. This will open a command prompt and start the script for you.

### **For macOS / Linux / Other Users**

1. Open your terminal or command prompt.  
2. Navigate to the wikidata-stats directory.  
3. Run the script using the following command:  
   python script/wikidata\_stats.py

### **Using the Tool**

Once the script is running, it will prompt you for the following information:

1. Wikidata username.  
2. Your choice of a date range (either a specific month or a custom range).  
3. The specific dates for your chosen range (e.g., 2024-07 or 2024-07-15).

The script will then fetch and process your contributions.

## **Output**

After the script finishes, it will print a report to the console and save it to a text file in the main wikidata-stats folder. The file will be named according to the user and date range, like so: wikidata\_stats-YourUsername-YYYY-MM-DD\_to\_YYYY-MM-DD.txt.

The content of the file will look like this:

User: YourUsername  
Period: 2024-07-01 to 2024-07-31  
Edited: 42  
Created: 5

## **How It Works**

The script uses the official Wikidata MediaWiki API to fetch a user's contributions. It determines whether a contribution is a "Created" or "Edited" item based on the following logic:

* A contribution is counted as **Created** if it is the very first revision of a page. The script identifies this by checking if the contribution's parentid (the ID of the previous revision) is 0\.  
* Any other contribution to a page in the main namespace is initially counted as an **Edited** item.  
* To ensure statistics are mutually exclusive, any page that was created during the period is removed from the "Edited" count, even if it was also edited by the user in the same period.

*This tool is not affiliated with or endorsed by the Wikimedia Foundation.*
