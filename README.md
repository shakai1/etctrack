Auditing /etc Directory Security and Monitoring 
This project focuses on securing the /etc directory by using auditd to track changes, setting up a daily cron job to process logs, and configuring mail server to send daily email alerts. This ensures any modifications to critical system files are logged and
reported

Ansible Playbook: Setting Up Auditd, Cron Job, and Sendmail

Install and Configure Auditd:
Install auditd: Ensures the auditd package is installed on the host.
Enable auditd: Configures auditd to start on boot and makes sure it is running.
Create audit rules file: Creates a rules file for audit if it doesn't exist.
Add audit rule for etc directory: Monitors all changes in the etc directory.
Restart auditd: Restarts auditd to apply new rules.

Setup Daily Cron Job:
 Copy script to cron.daily: Copies the log processing script to the daily cron job directory.
Enable cron service: Ensures the cron service is enabled and running.

Install and Configure mail server:
Install sendmail: Ensures mail daemon is installed.
Enable sendmail: Configures mail server to start on boot and ensures it is running.

Install Mail Utilities:
Install mailutils: Ensures mail utils is installed for email functionalities.

Configure Log Rotation:
Log rotation for auditd logs: Sets up log rotation to manage the size and retention of audit logs.

Bash Script: etcaudit-mailer
The etcaudit-mailer script processes the audit log to detect changes in the /etc directory and sends an email report of these changes.

parse_audit_log():
Reads audit logs: Reads /var/log/audit/audit.log and extracts entries for the current date.
Identifies file actions: Captures created, deleted, and edited files.
Gets usernames: Associates actions with usernames using the user ID.

email_output():
Sets email details: Defines the recipient, subject, and sender email details.
Sends email if changes detected: Sends the parsed log data via email if changes are found. If nothing has changed in the etc directory, not alerting email will be sent.
