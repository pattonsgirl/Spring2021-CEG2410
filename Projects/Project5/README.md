# Project 5 - NOT FINALIZED

## Advice & Resources

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

## Project Deliverable

- Create a folder called `Windows` in your repository for the course.  Project documentation should be in a file named `ad-setup.md`
- You may enjoy using MobaXTerm for the RDP connections to the Windows servers.  It can help with password management.

## Part 1: Create Windows Instances
- NOTE: unlike before, these instances will only take about 5 minutes to be accessible.  Yay!
- You already have a Key in AWS, and you already have the key that was downloaded to your system.  You don't need to create a new Key in AWS.
- [Sign in to AWS Educate](https://www.awseducate.com/student/s/)
- [Click here to provision your new stack](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=ceg2410-windowsAD&templateURL=https://cf-templates-bmjurcpfd9d8-us-east-1.s3.amazonaws.com/2021090XO5-windows-startup.yml)
- This link autofills many fields for creating our virtual machine.
  - On the first menu, click Next
  - On the second menu, under Parameters, type the name of the key pair you made in the  
    step above. If you don't remember, you can [open your key list here](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs:sort=keyName). Click Next
  - On the third menu, select Next
  - Scroll to the bottom and select Create Stack
  - You will be redirected to a status page that says CREATE_IN_PROGRESS
- In the [Running Instances](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceState) menu, click the checkbox next to `Windows AD Server`
- A description menu will open up below.
- Identify the Public IPv4 Address in the middle column. This is the IP address you will need to connect to the machine via Remote Desktop
- In the `Actions` tab (top right-ish), select `Security` then select `Get Windows password`
  - You will be prompted to upload or copy the contents of the key that was downloaded in the "Key Pair" step. Do so
  - Select `Decrypt Password`
  - The displayed password is the password for the account to log in to the Windows Server. Copy it to somewhere secure.

## Part 2: Set Up AD Server
1. Write the IP address of your Windows AD server.
2. Write the following information about your network connection:
  - The private IP
  - The subnet (not in CIDR notation)
  - The gateway IP 
  - The DNS server the system is configured to use
3. Install Active Directory on the server via the following Powershell command:
  - `Install-windowsfeature -name AD-Domain-Services -IncludeManagementTools`.  Note that this may need a system reboot.
4. Open Server Manager via the Start Menu.  You should see an action indication flag in `Notifications`.
5. Click the Configuration needed link in order to start configuring AD.  This should crop up with a friendly wizard.
6. What radio button most appropriately reflects what you are setting up?  You are creating your own infrastructure and their are no previously existing resources.
7. Write the name you would like for your domain.  Note that this is all on a private network, so you shouldn't be able to create a name conflict.
8. Write the NETBIOS name.  Note that NETBIOS names typically do not have the .com / .anything, and stick to the core name.
9. You should see some notifications in regards to DNS detection.  What is happening here is twofold:
  - AD would like to know if it should be a DNS server.  We want to keep this enabled, as in we can have our AD server be the DNS server for our private subnet.
  - AD is seeing if there are existing DNS servers on your private network, and if so, if it should reference it.
10. Set up administrative password.  
11. Finish the install process.  This may need a system reboot once complete.
12. Once you are back in, you may see that you are no longer connected to the private network.  This is nothing to panic about, but we do need to go manually configure our IPv4 settings via the Network Manager.
  - What DNS server address has been added to your network settings?  What is that address?
  - Fill in the rest of the connection information per your notes in question 1 of Part 2. Add the AWS default DNS server as an Alternate DNS Server.
  - Once you save these settings, it may cause loss of connection for your RDP connection.  Close the session and create a fresh connection.
13. Back in Server Manager, go to Tools, then open `Active Directory Administrative Center`.
14. Screenshot your success.

## Part 3: Create OUs
1. In your Windows AD Server, open `Active Directory Administrative Center`.
2. Create at least two OUs for your domain.  
  - Note: Users and Computers are "taken" - they are not good OU names, they already exist in AD to contain all users and all computers respectively.
3. Describe your OUs and the names you selected / intent of the structure you are creating.
4. Screenshot your success.

## Part 4: Add Users to AD

## Part 5: Add Computer to AD

- In the [Running Instances](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceState) menu, click the checkbox next to `WS 2016 Machine`
  - Note: AWS won't let us create Windows 10 instances.  Bummer.  But we can set up server instances.  Just because you have a server does NOT mean you have to install Active Directory on it.  You can use a server for whole bunches of other stuff.  We are going to use it like an everyday Windows machine.
- A description menu will open up below.
- Identify the Public IPv4 Address in the middle column. This is the IP address you will need to connect to the machine via Remote Desktop
- In the `Actions` tab (top right-ish), select `Security` then select `Get Windows password`
  - You will be prompted to upload or copy the contents of the key that was downloaded in the "Key Pair" step. Do so
  - Select `Decrypt Password`
  - The displayed password is the password for the account to log in to the Windows Server. Copy it to somewhere secure.

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.

