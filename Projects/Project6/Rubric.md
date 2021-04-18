# Project 6 Rubric

/ 16 

EC 1: / 1.6
EC 2: / 1.6

## Create and Connect to a File Share using `nfs`

- file called `nfs-config-guide.md` in the main folder of your repository
1. Install `nfs-kernel-server` write the command you used.
2. Create a directory on the server (the folder you'll be sharing).  Write the command you used.
3. Who is the user `nobody`?  Can `nobody` login to the system via a shell (ssh)?  Why is it used for `nfs` shares?
4. Change the owner of the folder to be shared to `nobody` and change the group to be `nogroup`.  Write the command(s) you used.
5. Figure out what ports `nfs` uses by default.  What two ports are they?
6. Enable the ports in your AWS Security Groups
    - **_Screenshot your updated inbound Security Group rules_**
7. Create a new Linux instance in AWS - this will be your client.  Write the public / elastic IP address of the client machine.
8. What is the `/etc/exports` file?
9. Back in the host machine, where you made the file to share, add a line similar to the following to `/etc/exports`
    - `/path/to/your/folder/to/share CLIENT_PUBLIC_IP(rw,sync,no_subtree_check)`
    - Write the line you added.
    - Define the parameters:
      - `rw`
      - `sync`
      - `no_subtree_check`
10. SSH in to the client machine.  Write the command you used.
11. Install `nfs-common`.  Write the command you used.
12. Create a folder on the client machine - this is where you'll be mounting the host folder to.  Write the command you used.
    - Note: you may need to use `sudo` depending on where you'd like the folder.
13. Mount the shared folder to your client's folder using a command similar to the following:
    - `sudo mount HOST_PUBLIC_IP:/path/to/shared/folder /path/to/client/folder`
    - Write the command you used
14. Run `df -h` - has your share been mounted?  How much space is available?
15. `cd` to the folder, and add some files with some text.  Don't change permissions (so may need `sudo`).  Screenshot your folder contents.
16. Go back to the host machine, and go to the shared folder.  Can you see the files created by the host?  Screenshot the folder contents.

## Extra Credit: Backup Plan (10%)

Create a file called `backup-plan.md` in the main folder of your repository.

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