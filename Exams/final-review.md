# Final Review for CEG 2410
## Spring 2021

## Da Rules

Final: Friday, 4/30

- Available 8:00 AM to 11:59 PM
- 1 attempt, 2 hours once started
- Open note, open terminal

## Topic List:

### User Accounts & Directory Services
- PAM - pluggable authentication module
    - by default looks at /etc/passwd & /etc/group
    - can install modules to use other authentication directories, like LDAP servers
- LDAP - Lightweight directory service
    - Note: these definitions are no different than AD, but we didn't end up playing with hardware (like adding computers) in LDAP
    - Domain component / controller
    - Organizational unit
        - logical subdivision of the domain (HR, server room, etc.)
    - Groups 
        - clusters of users
        - group names can have consquences in systems that use the name by default - by creating an "admin" group they can perform actions already defined on Linux systems for members of the "admin" group
    - Object classes
        - schemas that define properties of objects (users, computers, etc.)
- Active Directory
    - Active Directory Directory Services fully utilize LDAP for user / hardware management
    - Kerberos - authentication module that improves authentication security.  Commonly used in AD authentication for users
    - Forest
        - Cluster of domain controller(s) and the trust between them
    - Domain controller
        - Controls aspects of a domain.  Can be configured to be redundant (part of a network of existing domains) or to help balance other domain controllers in some fashion.
    - Organizational units
        - units of resources (hardware) and / or users.  Can set groups to access hardware, can set admins (or groups of) to control OUs
        - Group policies are applied to OUs
    - Groups
        - applies to clusters of users, think admins vs students.  Can grant access rights based on group membership
    - Can configure an AD server to also be a DNS server - it's just a server, server's can do multiple things
    - DNS server needs to be setup so other computers can look for the domain
    - Group policies
        - Can be set locally (even non-domain computers) or within an OU on a domain 
        - Manipulate settings actually located in registry editor (once applied), but with a slightly easier to parse interface

### Web Server Management
- Discussion of renaming default admin portals for services
    - phpldapadmin is known, people see if you server responds.  By renaming, I'm making it harder to scan, thus upping protection a little
- HTTP
    - Port 80
    - default configuration when apache2 HTTP is installed
    - a2ensite & a2enmod
- HTTPS
    - Port 443
    - encrypts communication
    - requires TLS/SSL certificate
- Basic apache2 HTTP server configuration
    - Configure port 80 connections to redirect to HTTPS
    - Configure HTTPS to use certs stored on server
- TLS/SSL Certificates
    - Works by:
        - When browser connects to site, site shares cert and public key, session key created
        - Browser determines cert trust, sends site symmetric session key
        - Site decrypts session key, sends acknowledgement to browser, encrypted session starts
    - Validation - domain
    - Certificate authorities
    - Self signed certs
    - Browser trust & certificates

### OS Comparisons
- Difference in updates
- Difference in OS versions
    - Windows - OS enables / disables capabalities based on Edition
    - Linux - server can be made to desktop, and vice versa.  Different distros are focused on use cases
- Administrator & sudo

### File Servers
- why?
- nfs, samba, and sshfs
    - discussion of ports / security

### System Management
- Be able to discuss ports and access concerns
- RAIDS
    - striping
    - mirroring
    - parity
    - types: 0, 1, 4, 5, 6
- controlling services with systemctl
    - start, stop, restart, status
- backups, snapshots & clones
- Windows:
    - Registry editor
        - HKEY_CLASSES_ROOT - File associations (can be overwritten by HKCU)
        - HKEY_CURRENT_USER - Settings that are specific to the currently logged-in user (pulls from HKU)
        - HKEY_LOCAL_MACHINE - Settings that are specific to the local computer
        - HKEY_USERS - Subkeys corresponding to the HKCU keys for each user profile actively loaded on the machine, though user hives are usually only loaded for currently logged-in users
        - HKEY_CURRENT_CONFIG - Stores all of the information about the current hardware configuration
    - msconfig, msinfo, Task Manager

### Powershell
- modules / commands in verb-noun pairings
- default extension
- running a powershell script (account permissions): Set-ExecutionPolicy
- Get-Alias # shows linux/cmd aliases for Powershell modules



## Prior Topics: Expectation of Familiarity

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
