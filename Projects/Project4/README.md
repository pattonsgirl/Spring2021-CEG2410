# Project 4

## Advice & Resources

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

## SLAPD

Create a file named `slapd.md` in your `server-scripts` folder.  Here is where you will provide documentation for this portion of the project.  The minimum deliverables for this section are highlighted in bold.  If you don't reach the final goal (authenticating with the LDAP server) this will be all you have to argue for partial points.

In Pilot -> Content -> Projects, there is a document containing authentication and password details to an LDAP server.  This server has had its firewalls configured to allow external access to port 339, the default LDAP port for authentication.  You job is twofold: create a new user on the LDAP server and configure your AWS instance to use this server for authentication.

1. Log on to the LDAP server and create a new user and add it to one of the existing groups.  You are welcome to stick with the [Harry Potter theme](https://en.wikipedia.org/wiki/List_of_Harry_Potter_characters).  If you find yourself about to delete something, please contact me first.
    - **_Screenshot your creation of an entry (fields are filled, ready to hit apply)_**

2. Configure your AWS system to use this LDAP server for authentication.  Follow the guide thoroughly, such that if a user is signing in to the system for the first time, PAM is configured to create them a home directory.
    - [Guide to configuring a system to authenticate with an LDAP server](https://computingforgeeks.com/how-to-configure-ubuntu-as-ldap-client/)
    - [Notes on implications of different group names and how to restrict access to specified groups](https://www.digitalocean.com/community/tutorials/how-to-authenticate-client-computers-using-ldap-on-an-ubuntu-12-04-vps)
    - **_Document the following:_**
        - packages installed (not the installation screenshots)
        - files modified (not the contents, just a list of which files were edited)
            - reason each file was modified.  I'm looking for role of what the change(s) enables

3. Test the water.  Use `getent` to verify that you can query LDAP for a given username.  Use `su - username` to sign in as the user that you created on the LDAP server.
    - **_Screenshot switching to this user successfully_**

## Certifiable

Create a file named `https.md` in your `server-scripts` folder.  Here is where you will provide documentation for this portion of the project.  The minimum deliverables for this section are highlighted in bold.  If you don't reach the final goal (authenticating with the LDAP server) this will be all you have to argue for partial points.

1. Enable port 80 and port 443 in your AWS Security Groups
    - [Sign in to AWS Educate](https://www.awseducate.com/student/s/)
    - This link should take you directly to the [Security Groups for your Virtual Private Cloud Network](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#SecurityGroups:)
    - Click the check box for the security group named: `ceg2410-test1-LinuxSecurityGroup-*`
    - In the lower panel, click the `Inbound Rules` tab, then click `Edit Inbound Rules`
    - Click `Add Rule`
    - In the `Type` dropdown, select `HTTP`. In the `Source` dropdown, select `Anywhere`
    - Click `Add Rule`
    - In the `Type` dropdown, select `HTTPS`. In the `Source` dropdown, select `Anywhere`
    - Click `Save Rules` when done
    - **_Screenshot your updated inbound Security Group rules_**

2. [Install Apache HTTP](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-16-04)
    - Note: you can skip Step 2: Adjust the firewall 
    - Confirm your installation was successful by going to a web browser and typing in the IP address for your AWS instance.
    - **_Screenshot the status of `apache2` using `systemctl`_**

3. Instead of displaying the default new installation page, have it display something you want.  There is an `index.html` file in this project directory you are welcome to use.
    - Note: You can use something else.  You can make it fancier.  You can use something from CS 2800.  Beauty and complexity are not in scope here ;)
    - **_Screenshot your new index.html page showing instead of the default_**

4. You are currently using defaults, which includes using HTTP for your site.  However, people expect encrypted interaction with sites these days, so you are going to create a cerification for your web server and have the site redirect connections to HTTPS.
    - Choose a certificate method:
        - [`openssl` - Documentation is within this tutorial under the section header `Create an SSL Certificate`](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server)
        - [`Let's Encrypt + cerbot`](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-16-04)
        - Note: wherever "domain" is referenced, you are just going to use the IP address of your AWS instance
    - **_Screenshot cert creation_**
    - Enable the `ssl` module for apache
    - Configure apache HTTP Virtual Host to redirect to https://your_ip
    - **_Screenshot your modified configuration file_**
    - Configure apache HTTPS Virtual Host to use your cert
    - **_Screenshot your modified configuration file_**
        - Hint: Guides to all three of these steps are [here under `Secure Apache` and `Configure the HTTP Virtual Host` and `Configure HTTPS Virtual Host](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server) 
    - Restart apache 
    - Refresh your browser and see if you need to validate the cert.
    - **_Link to your site_**

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.

### Instructor notes to self & configuration guides for server side

- [Install guide to create a SLAPD + phpldapadmin server](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps)
    - [Recommendations for configuring and protecting phpldapadmin](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server)
    - [Future TODOs: add configuration to authenticate with key pairs](https://serverfault.com/questions/653792/ssh-key-authentication-using-ldap)
