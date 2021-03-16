# Project 4 Rubric

/ 14 pts

## SLAPD - / 6 pts
- `slapd.md` in your `server-scripts` folder
- Screenshot your creation of an entry (fields are filled, ready to hit apply) on directory server https://3.95.41.145/dummyldap/
- Configure your AWS system to use this LDAP server for authentication with documentation of the following:
    - packages installed (not the installation screenshots)
    - files modified (not the contents, just a list of which files were edited)
    - reason each file was modified.  I'm looking for role of what the change(s) enables
- Screenshot switching to user created on directory server successfully

## Install web server software, certify it, and redirect traffic to HTTPS - / 8 pts

- `https.md` in your `server-scripts` folder
- Screenshot your updated inbound Security Group rules enabling ports 80 and 443 via world access
- Screenshot the status of `apache2` using `systemctl`
- Screenshot your new index.html page showing instead of the default
- Documentation for using HTTPS instead of HTTP
    - Screenshot cert creation
    - Screenshot your modified HTTP Virtual Host configuration file
    - Screenshot your modified HTTPS Virtual Host configuration file
    - Link to your site

## Extra Credit: / 1.4 pts
- Used index.html (default site) instead of following phpldapadmin guide to a t