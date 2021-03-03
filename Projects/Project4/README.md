# Project 3


## Advice & Resources

When writing scripts, there are two ways to go about making sure you're on the right track.  When first learning, I recommend running each command on the command line, then writing it in your script if it worked.  If you've programmed before, you may remember that print statements are your best friend when it comes to debugging.

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

## SLAPD

Send them email with password
They create one new entry

Connect to system for slapd authentication
Verify connection

Client configuration: https://computingforgeeks.com/how-to-configure-ubuntu-as-ldap-client/
Client access restriction: https://www.digitalocean.com/community/tutorials/how-to-authenticate-client-computers-using-ldap-on-an-ubuntu-12-04-vps

Install guide to create a SLAPD + phpldapadmin server: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps
    Protecting phpldapadmin: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server
    Next step: configure for public keys: https://serverfault.com/questions/653792/ssh-key-authentication-using-ldap

## Certifiable

Enable 80 and 443 in SecurityGroup

Install Apache HTTP, provide homepage / index.html

Self-signed certificate

Direct traffic to HTTPS only
    Good demonstration: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.
