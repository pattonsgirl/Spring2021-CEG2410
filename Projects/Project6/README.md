# Project 6

## Advice & Resources

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

## Part 1: Create a File Share

**Note:** to clear up space on your Linux system in AWS, run: `sudo rm -rf /opt/anaconda3` This will get a lovely 3.3 GB back.
- Install `samba`

## Part 2: Connect to File Share

1. Figure out what ports `samba` uses by default.  What two ports are they?
  - See if you can figure it out from the output of `sudo netstat -tunlp`
  - [Here's a resource](https://www.varonis.com/blog/smb-port/) if stumped
2. Enable the ports in your AWS Security Groups
    - [Sign in to AWS Educate](https://www.awseducate.com/student/s/)
    - This link should take you directly to the [Security Groups for your Virtual Private Cloud Network](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#SecurityGroups:)
    - Click the check box for the security group named: `ceg2410-test1-LinuxSecurityGroup-*`
    - In the lower panel, click the `Inbound Rules` tab, then click `Edit Inbound Rules`
    - Use `Add Rule` to add the rules
    - Click `Save Rules` when done
    - **_Screenshot your updated inbound Security Group rules_**
3. 

## Part 2: Backup Plan

Create a file called `backup-plan.md` in the main folder of your repository.

Answer the following questions with some thought.  Most think of backups at an enterprise scale, but you really get an appreciation for backups once your own flow / life gets interrupted. 

1. Describe how you currently maintain backups of your work and files important to you. Be honest.  There are still things to be learned if you aren't currently doing anything. 
2. What redundancy does your method provide?
3. Are you backing up your operating system, or just files within?
4. What core programs do you use?  
5. How long would it take to get back up and running if your system died tomorrow?
6. Is this time reasonable?
7. What improvements can you make to your backup plan?

## Extra Credit (10%): 

- **Note**: this opportunity can be used on any Windows machine - the AWS Windows instances or your own machine.
- Create a Powershell script that outputs a file to the Desktop.  The file content's should be a timestamp (also using a Powershell command / module)  
- Use the registry editor to have this script run once at next reboot
  - [Hint](https://docs.microsoft.com/en-us/windows-hardware/drivers/install/runonce-registry-key)
- Specify either in a `README.md` file or in comments in the script what you edited in the Windows Registry to run the script on next reboot.
- Add your script to the `Windows` folder in your GitHub repo.

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.


