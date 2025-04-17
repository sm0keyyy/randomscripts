# Random Scripts

This repository contains a collection of miscellaneous scripts for various tasks.

## Scripts

### `tmpsizemonitor`

A Bash script that continuously monitors the size of top-level files and folders within the `/dev/shm` directory.

**Features:**

*   Displays the current size (in MB) for each top-level item in `/dev/shm`.
*   Tracks the peak size (in MB) reached and the timestamp when it occurred for each item.
*   Refreshes the display every second.
*   Handles cases where `/dev/shm` is empty.
*   **Optional:** Logs timestamped size information to a specified file (`--log <logfile>`).
*   **Optional:** Attempts to show associated Process IDs (PIDs) using `lsof` (`--show-pid`). Requires `lsof` to be installed (feature disabled with a warning if missing).

**Usage:**

```bash
./tmpsizemonitor [--log <logfile>] [--show-pid]

# Examples:
# Run normally
./tmpsizemonitor

# Run and log output to /var/log/shm_monitor.log
./tmpsizemonitor --log /var/log/shm_monitor.log

# Run and attempt to show PIDs
./tmpsizemonitor --show-pid

# Run with logging and PID display
./tmpsizemonitor --log /tmp/shm.log --show-pid
```
*(Ensure the script has execute permissions: `chmod +x tmpsizemonitor`)*
*(Ensure `lsof` is installed if using `--show-pid`)*
*(Ensure write permissions for the log file path if using `--log`)*

---

### `emptyfilefinder`

A Bash script designed to find and optionally delete 0 KB files within a specified directory structure. It takes the source directory to scan and a directory for log files as command-line arguments.

**Features:**

*   Scans a user-specified source directory for files with a size of 0 KB, ignoring hidden files.
*   Categorizes found files into "TV Shows", "Movies", or "Other" based on keywords in their path (e.g., `/tv/`, `/movies/`).
*   Generates a report (`emptyfiles_report.txt`) listing the filenames in each category within a user-specified log directory.
*   Provides a summary count of empty files found in each category.
*   Includes a `--dry-run` option to simulate deletion without removing files.
*   Offers an interactive option to delete the found empty files (when not in dry run mode).
    *   Creates a temporary list (`emptyfiles_to_delete.txt`) in the log directory.
    *   Requires double confirmation before deletion proceeds.
    *   Logs deletion successes and failures (or simulated deletions in dry run) to the main report file.
    *   Shows deletion progress in the terminal.

**Usage:**

```bash
./emptyfilefinder [--dry-run] <source_directory> <log_directory>

# Examples:
# Scan and prompt for deletion
./emptyfilefinder /path/to/your/media /path/to/your/logs

# Perform a dry run (list files that would be deleted)
./emptyfilefinder --dry-run /path/to/your/media /path/to/your/logs
```
*(Ensure the script has execute permissions: `chmod +x emptyfilefinder`)*
*(Ensure the log directory exists before running)*
