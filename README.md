# Nexus Request Logs Parser

## Overview

This Ansible playbook is designed to parse and analyze Nexus request logs. It can handle both single log files and multiple logs from a specified number of days. The script categorizes requests, counts HTTP methods and status codes, and provides a summary report.

## Variables

To customize the playbook, adjust the following variables in the `vars` section:

- **`log_directory`**: Path to the directory where Nexus logs are stored. Example: `/var/nexus/log`
- **`latest_log`**: Name of the most recent log file. Example: `request.log`
- **`custom_logs`**: Base name pattern for date-patterned logs. Example: `request-2024`
- **`days_back`**: Number of days back to fetch logs. Example: `3`
- **`process_multiple_logs`**: Set to `true` to process multiple logs; `false` to process only the latest log.
- **`tmp_directory`**: Directory for temporary files. Example: `/tmp`
- **`local_save_directory`**: (Optional) Directory on your local machine where you want to save the logs. Example: `/path/to/local/save`

## Usage

1. **Configure Variables**: Update the `vars` section with appropriate values for your environment.

2. **Run the Playbook**: Execute the playbook with the following command:
    ```bash
    ansible-playbook path/to/your/playbook.yml
    ```

3. **Review the Output**: Check the summary of request data in the output. If `process_multiple_logs` is `true`, the playbook will analyze logs from the past `days_back` days. If `false`, it will analyze only the latest log file.

## Optional Features

- **Local Log Saving**: If you set `local_save_directory`, the playbook will copy `individual_requests.log` and `machine_requests.log` to this directory.
- **Temporary File Cleanup**: The playbook can clean up temporary files from `/tmp` if enabled.

## Example Configuration

Here is an example of how to set the variables:

```yaml
vars:
  log_directory: "/var/nexus/log"
  latest_log: "request.log"
  custom_logs: "request-2024"
  days_back: 3
  process_multiple_logs: true
  tmp_directory: "/tmp"
  local_save_directory: "/path/to/local/save/directory"
