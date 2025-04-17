# Random Scripts

This repository contains a collection of miscellaneous scripts for various tasks.

## Scripts

### `tmpsizemonitor`

A Bash script that continuously monitors the size of top-level files and folders within the `/dev/shm` directory.

**Features:**

*   Displays the current size (in MB) for each item.
*   Tracks the peak size (in MB) reached and the timestamp when it occurred.
*   Refreshes the display every second.
*   Handles cases where `/dev/shm` is empty.

**Usage:**

```bash
./tmpsizemonitor
# or
bash tmpsizemonitor
```
*(Ensure the script has execute permissions: `chmod +x tmpsizemonitor`)*

---

### `emptyfilefinder`

A Bash script designed to find and optionally delete 0 KB files within a specified directory structure. It takes the source directory to scan and a directory for log files as command-line arguments.

**Features:**

*   Scans a user-specified source directory for files with a size of 0 KB, ignoring hidden files.
*   Categorizes found files into "TV Shows", "Movies", or "Other" based on keywords in their path (e.g., `/tv/`, `/movies/`).
*   Generates a report (`emptyfiles_report.txt`) listing the filenames in each category within a user-specified log directory.
*   Provides a summary count of empty files found in each category.
*   Offers an interactive option to delete the found empty files.
    *   Creates a temporary list (`emptyfiles_to_delete.txt`) in the log directory.
    *   Requires double confirmation before deletion proceeds.
    *   Logs deletion successes and failures to the main report file.
    *   Shows deletion progress in the terminal.

**Usage:**

```bash
./emptyfilefinder <source_directory> <log_directory>
# Example:
./emptyfilefinder /path/to/your/media /path/to/your/logs
```
*(Ensure the script has execute permissions: `chmod +x emptyfilefinder`)*
*(Ensure the log directory exists before running)*
