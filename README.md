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

A Bash script designed to find and optionally delete 0 KB files within a specified directory structure, potentially tailored for Unraid systems.

**Features:**

*   Scans a source directory (default: `/mnt/user/media/library`) for files with a size of 0 KB, ignoring hidden files.
*   Categorizes found files into "TV Shows", "Movies", or "Other" based on keywords in their path (e.g., `/tv/`, `/movies/`).
*   Generates a report listing the filenames in each category and saves it to a log file (default: `/mnt/user/storage/jake/emptyfiles.txt`).
*   Provides a summary count of empty files found in each category.
*   Offers an interactive option to delete the found empty files.
    *   Requires double confirmation before deletion proceeds.
    *   Logs deletion successes and failures to the main log file.
    *   Shows deletion progress in the terminal.

**Configuration:**

*   The `SOURCE_DIR` and `LOG_FILE` paths can be modified directly within the script if needed.

**Usage:**

```bash
./emptyfilefinder
# or
bash emptyfilefinder
```
*(Ensure the script has execute permissions: `chmod +x emptyfilefinder`)*
