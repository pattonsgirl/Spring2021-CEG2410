# AWS Setup Guide

You should have received an email regarding your AWS  
Educate account for this class. We will be using AWS to create virtual environments  
for you to use to complete the tasks given.

**Important Note:** This AWS environment only allows inbound access from following ports:

- 22

## Getting Started:

### Text Editors:

I recommend [Visual Studio Code](https://code.visualstudio.com/) as a cross platform solution (plus dark mode looks cool). You can also use any default text editor on your system (Notepad, Notepad++, or whatever Mac's have).

### Setup for Windows Users

1. Install WSL 2

- [Follow instructions on the Windows blog](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps)
- Common pitfalls:
  - Windows is not fully up to date.
  - Did not reboot **before** running the change version command
- After installing Ubuntu from the Windows store, open Ubuntu once
  - After the installion message finishes, you should be prompted to create a username and password

2. In later labs, you will need two terminals open. It is absolutely alright to open multiple instances of Ubuntu, but it can be convenient to have a "tab" based setup. I recommend `Windows Terminal` (can be found in the Windows Store) or `MobaXTerm` (installation instructions below)

3. Optional: [Download MobaXterm Home Edition: Installer Edition](https://download.mobatek.net/2062020111930940/MobaXterm_Installer_v20.6.zip)

- Extract the contents to your Desktop.
- Double-click to run the installer
- Once installed, run the program one time - this finishes the installation
- You can now delete the installation files
- Open Moba. You can now choose to run WSL Ubuntu _or_ Moba bash.
  - To change terminals, go to Settings -> Configuration. Select the Terminal tab. In the dropdown at the bottom, change from `bash` to `WSL Ubuntu`

4. If you **do not have administrative privileges** on the system, you will need to install MobaXTerm (step 3) and install Cygutils (instructions below) in order to perform the labs.

- In Moba, select the Packages icon at the top.
- Wait for the package menu to appear.
- In the search bar, type "cygutils". Select the package from the result listings
- Select Install / Update.
- Restart Moba. Start Local Terminal should work
- In the toolbar for Moba, go to Settings -> Configuration
- In the General tab, check the following two fields are populated with the following values:
  - Persistent home directory: `_MyDocuments_\MobaXterm\home`
  - Persistent root directory: `_MyDocuments_\MobaXterm\slash`

### Mac & Linux Users

- You should have a terminal already installed. Hunt it down ;)

## Before you start: Register for AWS Educate

You should have an email from AWS Educate to guide you through account creation.  
Note: The email was sent to your wright.edu email account

Once you have filled in the registration information and verified your email address, you will get an account  
approval email. For reference, mine took 2-3 minutes to arrive.

_Registration form warnings_:

- Make sure you set a graduation date IN THE FUTURE
  - For Spring 2021, I recommend using 12/30/2026
- The last field on the right is a Promotional Code field. Your autofill may mistake it for a  
  zip code and unhelpfully fill it out for you. Make sure the Promotional Code field is _blank_ (empty)

## Provision the lab environment in AWS.

Assuming you have registered for AWS Educate and have access to this class, perform the following:

- [Sign in to AWS educate](https://www.awseducate.com/signin/SiteLogin)

  - Click the `My Classrooms` Button
  - Click the blue `Go to classroom` button for _Design of Info Tech Systems_
  - Click the blue `AWS Console` button

  This will launch the AWS console  
  Note: If you were already logged in with your personal account, click the log out prompt and  
  log back in with your university account

  Your username in the top right should look something like this  
  `vocstartsoft/user236529=lastname.number@wright.edu`.

Create an SSH key pair to get to your virtual machine.

- Click the Services menu, then select EC2 under Compute  
  [EC2 service from the AWS console](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Home:)  
  In the center area you should see a list of all Resources you have available.  
  Right now they should all be 0.
- Click on [Key Pairs](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs:sort=keyName)
- Click on the `Create Key Pair` blue button.
  - Choose the name for your key. I used `ceg3120-aws-vm`  
    **MAKE SURE YOU SELECT SSH (pem) as the key type**
  - This creates a public/private key pair, stores the public key in AWS, and downloads the private key to your local machine.
  - **Do not lose the downloaded key.**
  - Back it up to a USB drive or your Office365 account. Once you go through the steps below, this key will be the only way to log in to your AWS environment. If the key is lost, you will need to delete the environment and start from scratch.

Create your AWS environment

- Once you have created your SSH key, [TODO - DO NOT CLICK UNTIL THIS MESSAGE IS GONE](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=CEG-2350&templateURL=https:%2F%2Fwsu-cecs-cf-templates.s3.us-east-2.amazonaws.com%2Fceg2350.yml)
  This link autofills many fields for creating our virtual machine.

  - On the first menu, click Next
  - On the second menu, under Parameters, type the name of the key pair you made in the  
    step above. If you don't remember, you can [open your key list here](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs:sort=keyName). Click Next
  - On the third menu, select Next
  - Scroll to the bottom and select Create Stack
  - You will be redirected to a status page that says CREATE_IN_PROGRESS

- Once you have created the AWS Cloud formation stack you can [return to the EC2 service](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Home:).  
  Here you should see additional resources have been created (not everything says 0 anymore)
- Click on [Running Instances](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceState)
- Our machine should now be created (or almost ready).
- Your machine will be assigned an Elastic IP address. This IP address is what we will use to SSH into the virtual environment.

**WARNING**
While exploring and discovery is an important part of this course, any additional resources you create in AWS have an associated charge. If resources besides those strictly asked for by this course stay running, you risk running out of funds for this course. While fixable, this will hinder your ability to complete projects on time.

## Connecting to the AWS environment

**You are now ready to make an SSH connection to your AWS server.**

- Open a terminal.
- Copy of the AWS SSH key that was downloaded to your home directory
  - Helpful commands: `cp, ls, man`
  - The manual method: Create a file with a useful name (or the same name as the downloaded file) `ceg3120-aws-vm.pem`
  - Open a text editor (`vim` or `nano`)
  - Copy and paste the contents of the key that was downloaded from AWS Educate into the file.
- Change the permissions on the key file in your directory
  - Because private keys need to be protected, the key needs to be changed to readable by your user by using `chmod`
  - `chmod 600 /path/to/private/key` - replace _/path/to/private/key_ with your information
  - Resource on how to use [chmod](https://www.howtogeek.com/437958/how-to-use-the-chmod-command-on-linux/)
- SSH into your AWS server with the following command  
   `ssh -i /path/to/private/key ubuntu@ElasticIP`  
   Note: replace _/path/to/private/key_ and _ElasticIP_ with your information
  - If your connection was refused, you may have forgotten to put the username `ubuntu` in front of your Elastic IP address
- You are now signed in to your AWS Educate system as the user `ubuntu`

## Git Going

1. Create or sign in to your [github](https://github.com/) account.
2. Create a new Repository with a name of your choice. I recommend `Spring2021-CEG3120`.
   - Set it to Private (you can change this in the future).
   - Check the box to Initialize this repository with a README
   - Click Create Repository
3. In your github repository, select Code (green button). It should say "Clone with HTTPS". Copy the URL to your clipboard.
4. SSH in to your AWS Educate environment.
5. Use the `git` command to `clone` your repository.

## Git Passwordless (If you want)

Note you will need to create the key pair on any system you want to use passwordless authentication on.

1. [Create a key pair, upload public key (.\*\.pub) to github](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
2. [Change your repo to authenticate with SSH (not HTTPS)](https://help.github.jp/enterprise/2.11/user/articles/changing-a-remote-s-url/)
3. [If you have errors, poke around here](https://docs.github.com/en/github/authenticating-to-github/error-permission-denied-publickey)

## Troubleshooting

### Destroying Excess Cloud Formations

1. Go to the Services dropdown, under Management and Governance, select CloudFormation
2. Select the unwanted Stack, then select Delete
   - It is important to remove old stacks. Each stack has a charge associated with it, so you risk running out of funds for this course. While fixable, this will delay your ability to complete labs on time.

### Remaking your AWS Educate environment

The steps below should only be needed if you lost your key from AWS Educate. If you still have your key but your enviromnent is broken, only follow steps 1-2, then go back to the instructions above and rebuild your stack.

1. Go to the Services dropdown, under Management and Governance, select CloudFormation
2. Select your Stack, then select Delete
   - It is important to remove old stacks. Each stack has a charge associated with it, so you risk running out of funds for this course. While fixable, this will delay your ability to complete labs on time.
3. Go to the Services Dropdown, under Compute select EC2
4. Select Key Pairs
5. Select your key pair(s) and select Delete.
6. Recreate your environment by following the steps above

### I have a Chromebook, and ssh in Terminal isn't working...

This guide here refers to a [Chrome Extension for SSH connections](https://www.lifewire.com/how-to-use-chromebook-ssh-client-4690108)

- To use your AWS Educate Private Key, you'll need to select "Import..." and browse to your  
  key file - you can then select your key from the dropdown.
- You may need to make a "failed" connection in order to get the permission to access files  
  questions to pop up.

### Acknowledgement

Credit to Matt Kijowski's GitHub Repo - [Lab 1 for Cyber Security Analysis](https://github.com/mkijowski/cyber-security-analysis-applied/blob/master/labs/lab1.md)
