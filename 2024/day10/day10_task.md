## Task

Write a Bash script that automates the process of analyzing log files and generating a daily summary report. The script should perform the following steps:

1. **Input:** The script should take the path to the log file as a command-line argument.

2. **Error Count:** Analyze the log file and count the number of error messages. An error message can be identified by a specific keyword (e.g., "ERROR" or "Failed"). Print the total error count.

3. **Critical Events:** Search for lines containing the keyword "CRITICAL" and print those lines along with the line number.

4. **Top Error Messages:** Identify the top 5 most common error messages and display them along with their occurrence count.

5. **Summary Report:** Generate a summary report in a separate text file. The report should include:
   - Date of analysis
   - Log file name
   - Total lines processed
   - Total error count
   - Top 5 error messages with their occurrence count
   - List of critical events with line numbers

6. **Optional Enhancement:** Add a feature to automatically archive or move processed log files to a designated directory after analysis.

## Tips

- Use `grep`, `awk`, and other command-line tools to process the log file.
- Utilize arrays or associative arrays to keep track of error messages and their counts.
- Use appropriate error handling to handle cases where the log file doesn't exist or other issues arise.

```
#!/bin/bash

# Check if log file path is provided as an argument
if [ -z "$1" ]; then
    echo "Usage: $0 <log_file_path>"
    exit 1
fi

LOG_FILE=$1

# Check if the log file exists
if [ ! -f "$LOG_FILE" ]; then
    echo "Error: Log file $LOG_FILE not found!"
    exit 1
fi

# Initialize variables
DATE=$(date +"%Y-%m-%d")
SUMMARY_REPORT="summary_report_$DATE.txt"
ERROR_KEYWORDS="ERROR|Failed"
CRITICAL_KEYWORD="CRITICAL"

# Count total number of error messages
ERROR_COUNT=$(grep -E -c "$ERROR_KEYWORDS" "$LOG_FILE")

# Find lines with "CRITICAL" keyword and store the line number with the content
CRITICAL_EVENTS=$(grep -n "$CRITICAL_KEYWORD" "$LOG_FILE")

# Get total lines processed
TOTAL_LINES=$(wc -l < "$LOG_FILE")

# Find top 5 most common error messages
TOP_ERRORS=$(grep -E "$ERROR_KEYWORDS" "$LOG_FILE" | sort | uniq -c | sort -nr | head -n 5)

# Create the summary report
{
    echo "Daily Log Summary Report - $DATE"
    echo "Log File: $LOG_FILE"
    echo "---------------------------------"
    echo "Total Lines Processed: $TOTAL_LINES"
    echo "Total Error Count: $ERROR_COUNT"
    echo
    echo "Top 5 Most Common Error Messages:"
    echo "$TOP_ERRORS"
    echo
    echo "Critical Events (Line Number: Event):"
    echo "$CRITICAL_EVENTS"
} > "$SUMMARY_REPORT"

echo "Summary report generated: $SUMMARY_REPORT"

# Optional: Move the log file to a processed folder after analysis
ARCHIVE_DIR="processed_logs"
mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR"

echo "Log file archived to $ARCHIVE_DIR/"


```
