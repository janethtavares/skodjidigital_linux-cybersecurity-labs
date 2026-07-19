# Session 02 – Linux Server Forensics

## Objective

Practice basic Linux server forensic investigation by accessing a remote machine via SSH and analysing authentication and Apache web server logs.

## Environment

- Platform: TryHackMe
- Room: Linux Server Forensics
- Environment: AttackBox + Lab Machine
- Connection method: SSH
- User: `fred`

## Tasks Performed

### 1. Connected to the Lab Machine via SSH

I connected from the TryHackMe AttackBox to the target Linux server using SSH:
After authenticating with the provided credentials, I successfully accessed the remote machine.

2. Navigated to the System Log Directory

I accessed the Linux log directory using:

cd /var/log/

This directory contains important system logs that can be analysed during a forensic investigation.

3. Investigated Failed SSH Login Attempts

I searched the authentication log for failed password attempts:

grep "Failed password" auth.log

The output showed a failed SSH authentication attempt, including information such as:

Username involved in the attempt
Source IP address
SSH service
Source port

This demonstrated how authentication logs can be used to identify suspicious or unsuccessful login activity.

4. Navigated to Apache Logs

I accessed the Apache web server log directory:

cd /var/log/apache2

I then listed the available log files:

ls

The directory contained files including:

access.log
access.log.1
error.log
error.log.1
other_vhosts_access.log

These logs can be used to investigate requests made to a web server, including source addresses, HTTP responses and user-agent information.

Key Learnings

During this lab, I practised:

Connecting securely to a remote Linux server using SSH
Navigating Linux system log directories
Using grep to search authentication logs
Identifying failed SSH login attempts
Locating Apache web server logs
Understanding how logs support basic digital forensic investigations
Lab Status

The practical lab was partially completed. I successfully completed the initial SSH access and authentication log analysis and reached the Apache log analysis section.

The TryHackMe AttackBox session expired before I could complete the remaining questions and tasks.

Conclusion

This exercise provided practical experience with Linux server forensics and demonstrated how authentication and web server logs can be used to investigate security-related events.

```bash
ssh fred@<LAB_MACHINE_IP>
