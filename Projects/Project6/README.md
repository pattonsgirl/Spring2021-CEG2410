# Project 6

## Advice & Resources

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

## Part 1: Create and Connect to a File Share using `nfs`

Create a file called `nfs-config-guide.md` in the main folder of your repository.  Ideally this will end up looking like a nice how-to guide, but you can also answer each question / step below in the file for grading.

- There are a million and one file share solutions out there - were going to go with one of the easier to set up ones, NFS.  The purpose of this is to set up a server that can host files, then configure systems (clients) to connect to the host.  NFS is not necessarly the best recommended solution for your future needs.  You could also investigate samba or sshfs, or DropBox or OneDrive, or an open source alternative [file hosting server](https://alternativeto.net/software/owncloud/?platform=self-hosted) with more browser / GUI features.
- [Reference material for creating and connecting NFS server in Linux](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-16-04)
- A neat comparision in performance between NFS, SMB (samba), and SSHFS [linked here](https://blog.ja-ke.tech/2019/08/27/nas-performance-sshfs-nfs-smb.html)

1. On you AWS Linux instance, install `nfs-kernel-server` write the command you used.
  - **LOW SPACE?:** to clear up space on your Linux system in AWS, run: `sudo rm -rf /opt/anaconda3` This will get a lovely 3.3 GB back.
2. Create a directory on the server (the folder you'll be sharing).  Write the command you used.
3. Who is the user `nobody`?  Can `nobody` login to the system via a shell (ssh)?  Why is it used for `nfs` shares?
    - [Hint](https://unix.stackexchange.com/questions/186568/what-is-nobody-user-and-group)
4. Change the owner of the folder to be shared to `nobody` and change the group to be `nogroup`.  Write the command(s) you used.
5. Figure out what ports `nfs` uses by default.  What two ports are they?
    - [Here's a resource](https://library.netapp.com/ecmdocs/ECMP1155586/html/GUID-C764CE34-6F5B-42BC-B04B-7001744A44A3.html)
6. Enable the ports in your AWS Security Groups
    - [Sign in to AWS Educate](https://www.awseducate.com/student/s/)
    - This link should take you directly to the [Security Groups for your Virtual Private Cloud Network](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#SecurityGroups:)
    - Click the check box for the security group named: `ceg2410-test1-LinuxSecurityGroup-*`
    - In the lower panel, click the `Inbound Rules` tab, then click `Edit Inbound Rules`
    - Use `Add Rule` to add the rules
    - Click `Save Rules` when done
    - **_Screenshot your updated inbound Security Group rules_**
7. Create a new Linux instance in AWS - this will be your client.  Write the public / elastic IP address of the client machine.
    - [Steps to create new instance](#Steps-to-Create-New-Instance)
8. What is the `/etc/exports` file?
    - [Hint](https://man7.org/linux/man-pages/man5/exports.5.html)
9. Back in the host machine, where you made the file to share, add a line similar to the following to `/etc/exports`
    - `/path/to/your/folder/to/share CLIENT_PUBLIC_IP(rw,sync,no_subtree_check)`
    - Write the line you added.
    - Define the parameters:
      - `rw`
      - `sync`
      - `no_subtree_check`
10. SSH in to the client machine.  Write the command you used.
11. Create a folder on the client machine - this is where you'll be mounting the host folder to.  Write the command you used.
    - Note: you may need to use `sudo` depending on where you'd like the folder.
12. Mount the shared folder to your client's folder using a command similar to the following:
    - `sudo mount HOST_PUBLIC_IP:/path/to/shared/folder /path/to/client/folder`
    - Write the command you used
13. Run `df -h` - has your share been mounted?  How much space is available?
14. `cd` to the folder, and add some files with some text.  Don't change permissions (so may need `sudo`).  Screenshot your folder contents.
15. Go back to the host machine, and go to the shared folder.  Can you see the files created by the host?  Screenshot the folder contents.

## Extra Credit: Backup Plan (10%)

Create a file called `backup-plan.md` in the main folder of your repository.

Answer the following questions with some thought.  Most think of backups at an enterprise scale, but you really get an appreciation for backups once your own flow / life gets interrupted. 

1. Describe how you currently maintain backups of your work and files important to you. Be honest.  There are still things to be learned if you aren't currently doing anything. 
2. What redundancy does your method provide?
3. Are you backing up your operating system, or just files within?
4. What core programs do you use?  
5. How long would it take to get back up and running if your system died tomorrow?
6. Is this time reasonable?
7. What improvements can you make to your backup plan?

## Extra Credit: Powerplay (10%): 

- **Note**: this can be done on any Windows machine - the AWS Windows instances or your own machine.
- Create a Powershell script that outputs a file to the Desktop.  The file content's should be a timestamp (also using a Powershell command / module)  
- Use the registry editor to have this script run once at next reboot
  - [Hint](https://docs.microsoft.com/en-us/windows-hardware/drivers/install/runonce-registry-key)
- Specify either in a `powershell-notes.md` file in your `Windows` folder or in comments in the script what you edited in the Windows Registry to run the script on next reboot.
- Add your script to the `Windows` folder in your GitHub repo.

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.

## Steps to Create New Instance

You already have a Key in AWS, and you already have the key that was downloaded to your system.  You don't need to create a new Key in AWS.

- [Sign in to AWS Educate](https://www.awseducate.com/student/s/)
- [Click here to provision your new stack](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=ceg2410-316mods&templateURL=https://cf-templates-bmjurcpfd9d8-us-east-1.s3.amazonaws.com/20210750FQ-linux-startup.yml)
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


