## Written answer: (8 pts)

1. What RAID level / number would be most appropriate for needing to support failure of two disks without data loss.  Describe how the disk array is set up to enable this capability.
    - RAID 6 / RAID level 6
    - each disk contains two parity blocks which are stored on different disks across the array

2. I have a service that needs to run over port 56.  What should I consider when determining network security rules for allowing access to this port?
    - who needs access?
    - define security rules (firewalls) that specify IPs/ ranges of IPs (subnets) that are allowed to access the port

3. I just installed a fileshare (nfs) and need to figure out if it's working or not (because right now, it's not).  Describe two things I should check.
    - configuration file
    - service status
    - firewall ports
    - file permissions
    - from client 
        - use `nmap -Pn server_name_or_IP` will tell you if server is showing the open port
        - check local name service (mispelling or incorrect IP)
    - `ping`ing servers is not always a guarantee that a service is up.  Pinging is also disabled in most cases these days.  If this system responds to a ping, the most information you have is that the system is reachable from one network to another. `telnet`, however, could be used to check a specific port. `tcptraceroute` or `traceroute` can have a port specified.  It won't tell you what is wrong, but may give a hint that you need to look at firewalls.
    - as stated, the server is currently not working, so `df -h` or just trying to store files would not tell me what's happening, just that it is broken.

4. While browsing for varieties of hellebores I go to helleboresdirect.com.  My browser displays "Your connection is not private
Attackers might be trying to steal your information from helleboresdirect.com (for example, passwords, messages, or credit cards)."  What is a possible cause of this message?
    - cert invalid
    - cert expired
    - cert was self signed, not trusted by browser
    - This message will only display if HTTPS was enabled but the browser cannot verify the certificate.  Sites can be configured to use HTTP - search engines may bias against them in results, but the page would still display if it only had HTTP and no HTTPS configuration.
    - time out of sync
    - antivirus software

5. Describe all steps needed to enable and configure HTTPS on a webserver.
    - add / enable module
    - redirect HTTP requests to HTTPS
    - get SSL / TLS cert
    - configure HTTPS with corresponding cert
    - restart web server service with new configuration
    - open the firewall(s) for port 443
 
## Written commands / code

1. Write a command that restarts the apache2 service (no reboots).
    - `systemctl restart apache2`

2. Write a command to update packages in Ubuntu Linux.
    - `apt update` OR `apt-get update`
    - `apt upgrade` upgrades packages IF an update was fetched / marked available

3. Find a Powershell module that will show the end of a file instead of the whole file.  In Linux, it would be the `tail` command.  Cite your source.
    - `Get-Content C:\example.txt -Tail 25`
    - sources: various
    - `-wait` is kind a of living tail or echo - for it to work, you have to go update the file, then wait will show something
    - when seeking answers like this, reference two sources (or more) - you get a more universal feel for what people would use and a confirmation that you're in the right direction.

4. Describe a strategy to add a picture and have it display in a .md file (like README.md) in GitHub.
    - Open GitHub, click "edit" / pencil button for `.md` file, copy / paste image.  Auto creates markdown syntax and uploads file.
    - Locally, add file to repo (or in folder in repo).  In `.md` file, add markdown ![Alt text](relative_path_to_image).  add, commit, and push
    - Create "Issue" in GitHub and add photo to issue, then use link in markdown

5. Given the following line from a terminal, how can I edit the file listed (bar.txt)?
```
kduncan@P-747827AD5219:~/foo$ ls -lh
-rw-r--r-- 1 root root 0 Apr 29 17:42 bar.txt
```
    - use `sudo`
    - change permissions of file to `kduncan`
    - add `kduncan` to `root` group
    - open permissions for `other` / all users to have edit permissions.

## Fill in the blank

1. In what registry key (HKEY_...) are settings for all users with accounts on the system?
    - HKEY_USERS - has all user settings for any account, loads into HKEY_CURRENT_USER when there is a log in
    - HKEY_LOCAL_MACHINE - Contains configuration information particular to the computer (for any user)

2. In a domain, ____ are ways to organize users for access permissions to files / folders and can help organize clusters of administrators over an organization unit.
    - groups

3. ____ servers manage records of IPs to hostnames.  If your system is hosting this service and additional services, you need to add this server to the network settings so that the hostnames can be mapped to their IP addresses.
    - Domain Name Servers / System

## True / False

1. You should not test your backups until you need them in an emergency.
    - False, backups should be tested at some frequency so that they are known to be reliable in an emergency.

2. While browsing for varieties of hellebores I go to helleboresdirect.com.  My browser displays "Your connection is not private
Attackers might be trying to steal your information from helleboresdirect.com (for example, passwords, messages, or credit cards)."  I should proceed in my plan to buy 100 hellebores from this site.
    - False.  If the cert is not trusted, there are a variety of potential problems.  

3. If HTTPS is enabled for a site, the browser gets a copy of the site's pubic key of the site's SSL / TLS key.
    - True

4. Within a domain, all users must have a unique identifier.
    - True