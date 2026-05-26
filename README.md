**Realistic Terminal Operations Lab — Overview & Introduction**

This lab is a complete hands-on terminal, system administration, scripting, and SOC investigation environment designed to simulate real-world cybersecurity and Linux operational tasks. Instead of relying only on Splunk searches, this lab focuses on learning how analysts and administrators interact directly with raw logs, configuration files, scripts, backups, cron jobs, network information, and incident evidence through the terminal.

The purpose of this lab is to build practical experience with core Linux and terminal-based tools commonly used in:

Tier 1 SOC operations\
Tier 2 SOC investigations\
Incident response\
System administration\
Log analysis\
Threat hunting\
Basic DevOps and scripting workflows

The dataset contains realistic simulated enterprise infrastructure data, including:

SSH authentication logs\
Firewall logs\
Web server logs\
SQL injection activity\
System logs\
Application logs\
User/account information\
Security configurations\
Bash and Python scripts\
Cron scheduled tasks\
Mock web application files\
Asset inventory data\
Threat intelligence and IP reputation data\
Incident response templates\
Risk assessment documentation

Throughout this lab, we will use terminal tools to investigate security events, identify suspicious behavior, analyze attacker activity, review configurations, automate tasks, and simulate real SOC investigation workflows. The environment was intentionally structured like a small enterprise network so that every command has practical investigative value rather than isolated command practice.

We will work with many important Linux and terminal tools, including:

ls, cd, pwd

cat, less, head, tail\
grep, awk, sed\
sort, uniq, cut, wc\
find, xargs\
chmod, tar, zip\
ps, top, df, du\
bash, python3\
git\
curl\
crontab

The lab also introduces incident response concepts such as:

failed login investigations\
brute-force detection\
suspicious account activity\
persistence techniques\
SQL injection analysis\
large outbound transfer detection\
attacker IP correlation\
timeline reconstruction\
evidence collection and reporting

This lab directly interact with the raw source files themselves.

The overall goal is to build a ready portfolio of terminal-based cybersecurity investigations and operational workflows that demonstrate practical experience in:

Linux administration\
SOC operations\
incident response\
log analysis\
scripting\
investigation methodology\
operational security analysis

This lab will serve as both a learning environment and a practical demonstration of hands-on cybersecurity skills.

**Cd:** Changes directory (moves you into a folder).

cd ~/Downloads/realistic_terminal_ops_lab

pwd: Shows your current directory/location.

**ls**

Lists files and folders inside current directory.\
There are the folders

logs\
scripts\
configs\
users\
reports\
webapp\
network

**ls -lh**

Lists files with readable sizes and permissions.

**cd logs**

Moves into logs directory.

**pwd**

Shows current location again.\
Inside /logs

**ls**

Shows log folders.

auth\
web\
firewall\
system\
app

**cd auth**

Moves into authentication log directory.

**ls**

Shows files in auth directory.\
auth.log

**cat**

Displays file contents.\
Using: cat auth.log in the terminal bash\


**less**

Opens large files page-by-page for easier reading.\
Using: less auth.log in the terminal bash

Inside less
There is

**head**

Shows first lines of a file.\
\
Using: head auth.log

**tail**

Shows last lines of a file.

Using: tail auth.log in the terminal

SOC analysts use them to quickly:

inspect beginning of logs\
inspect latest activity\
check newest attacks/events

**grep**

Searches for matching words/patterns.

Using: grep "failed" auth.log in the terminal

We are now searching for:

action=failed

which usually means:

failed login attempts\
brute force attempts\
suspicious access activity

**Count Failed Logins**

Counts matching lines.

Using: grep "failed" auth.log \| wc -l

searching failed events\
sending results through pipeline \|\
counting total events

Search Specific Attacker IP


Searches activity from one suspicious IP.

Using: grep "203.0.113.45" auth.log


We are investigating:

203.0.113.45 which is one of the suspicious attacker IPs inside the dataset.

------------------------------------------------------------------------

# Count Attacker Activity

Counts how many events came from attacker IP.

Using: grep "203.0.113.45" auth.log \| wc -l


# Extract Only Failed Events from Attacker

Using: grep "203.0.113.45" auth.log \| grep "failed"


This is real investigation workflow:

identify suspicious IP\
isolate activity\
identify failed attempts\
build timeline


# awk

Extracts/selects specific columns or fields.

Using: grep "203.0.113.45" auth.log \| awk '{print \$1,\$2,\$6,\$7}'


**Find Successful Logins**

Searches successful SSH logins.

Using: grep "accepted" auth.log

This comparing failed logins VS successful logins to detect:

brute force success\
compromised accounts

**Investigate User test**

Using: grep "user=test" auth.log

**Sort Events by Time**

Sorts matching events chronologically.

Using: grep "user=test" auth.log \| sort

Analysts reconstruct:

what happened first\
what happened next\
persistence activity\
escalation activity

**Find Persistence Activity**

Searches for SSH persistence modification.

Using: grep "authorized_keys" auth.log

Attackers often:

add SSH keys\
maintain persistence\
return later without passwords

**Move Back to Main Lab Directory**

Moves back to main project root.

Using: cd ~/Downloads/realistic_terminal_ops_lab

**View Firewall Logs**

Moves into firewall logs.

Bash:\

cd logs/firewall\
ls\
cat firewall.log

Ppease refer to imades in the repository for output.
