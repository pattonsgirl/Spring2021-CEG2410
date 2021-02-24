# Midterm Review for CEG 2410
## Spring 2021

## Da Rules

Midterm: Friday, 2/26

- Available 8:00 AM to 11:59 PM
- 1 attempt, 2 hours once started
- Open note, open terminal
- No class - only exam


## Topic List:

### git basics:
- clone
    - followed by a URL / ssh link copy of what is on GitHub and a link back to the GitHub repository (remote)
- add
    - adds a file for tracking.
- commit
    - creates a snapshot of the repository with any changes, require a message to say what changed
- push
    - get local commits / snapshots of changes to our remote repository (GitHub)
- status
    - give me hints about whats happening in repository

### Networking:
- Public vs private ips
- Routers
    - NAT
    - Firewall
    - DHCP
- DNS
- CIDR notation (and translating to subnet masks or vice versa)
    - 130.108.0.0/16 - 130.108.0.0 - 130.108.255.255 - 130.108.0.0 subnet 255.255.0.0
    - 231.121.56.23 / 24 - 255.255.255.0 (corresponding subnet mask)
- Ports
    - default ports and their services
    - When a port should be open vs closed
- Firewall (at machine level and overarching level)
    - INBOUND
    - OUTBOUND
    - FORWARD
- SSH
    - ssh to remote in to a machine - secure encrypted traffic connection to that machine
    - ssh keys for authentication
    - key pairs (public vs private keys)
        - private keys are just for me, public keys are added / uploaded to the machine I am connecting to

### Linux management:
- Basic commands:
    - man, ls, cd, mkdir, rm / rmdir
- Package management with `apt`
- Permissions
    - owner / user, group, other (ugo)
    - read, write, execute (rwx)
    - role of sudo
    - chown, chgrp, chmod
- Scripting for automation of tasks (bash)
    - variables - var_name=45 $var_name
    - permissions needed to run
    - user input
    - using the `test` command ([])
    - if statements
    - for and while loops
        - syntax, surrounding with do's and done's
    - functions
    - arguments
- regular expressions for pattern matching
    - grep -E -o "pattern here" input_file 
- cron 
    - settings for how often (minute hour day-of-the-month month-of-the-year day-of-the-week), or pre set frequency (@reboot, @daily, etc)
    - what is needed to set email
- iptables
    - consequences of chains

### Emails
- POP vs IMAP
    - POP clients are going to have individual tracking and updates of emails
    - IMAP clients are synced with what is happening with your mailbox
- Configuration
    - email with smtp
        - what port?

### Disk managment
- Clean up disk space
    - checks logs / temp files
    - old kernels?
    - unused packages
