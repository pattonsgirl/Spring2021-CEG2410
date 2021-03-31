# Project 5 - NOT FINALIZED

## Advice & Resources

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

If you mess something up along the way and lock yourself out of your system, it's going to be easiest to create a fresh environment.  See the [Troubleshooting](#Troubleshooting) section at the end of this write up for a quick version.

## Window in to Windows

windows-startup.yml
Post to S3 and make public (remember this is two steps)

Install Powershell module for VS Code - may prompt to install additional packages.  Select Yes where prompted
  - Powershell ISE is being phased out

Powershell script that outputs a file to the Desktop.  Use the registry editor to have this script run once at next reboot

https://docs.microsoft.com/en-us/powershell/scripting/dev-cross-plat/vscode/how-to-replicate-the-ise-experience-in-vscode?view=powershell-7.1

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.

## Troubleshooting
TODO: Fix wording for AWS, otherwise links are good

So you locked yourself out and need to create a fresh system.  No worries, this section has your back.  We are going to do very similar steps to what we did in the beginning, but with some shortcuts.

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
- Go to the EC2 menu and click on [Running Instances](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceState)
- Click the checkbox next to `Linux Server 16_04`
- A description menu will open up below.
- Identify the Public IPv4 Address in the middle column. This is the IP address you will need to connect to the machine via SSH