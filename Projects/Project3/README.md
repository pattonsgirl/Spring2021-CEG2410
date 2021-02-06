# Project 3


## Advice & Resources

When writing scripts, there are two ways to go about making sure you're on the right track.  When first learning, I recommend running each command on the command line, then writing it in your script if it worked.  If you've programmed before, you may remember that print statements are your best friend when it comes to debugging.

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

**Resources**
- [Regex101](https://regex101.com/)
    - [Learn RegEx with mini-challenges](https://regexone.com/)
- [`sed` tutorial to manipulate text](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)


### [You've got the magic in you](https://www.youtube.com/watch?v=DqMZ8TieXfU&ab_channel=puddles235)

A very common task as a sys admin is dealing with data.  Specifically, data that needs cleaning up in some fashion - ethier by getting out a specific set of info, cleansing bad data, etc.  

- In the main folder of your repository, create a folder called `file-scripts`
- Using `wget` download this file to your folder:
    - https://raw.githubusercontent.com/pattonsgirl/Spring2021-CEG2410/main/Projects/Project3/list.txt
- Use `sed` or another method of your choice to parse out **only the emails** from `list.txt`  Do not overwrite `list.txt`, instead save them to a file called `list-emails.txt`
- Use `sed` or another method of your choice to parse out **only the ids** from `list.txt`  Do not overwrite `list.txt`, instead save them to a file called `list-ids.txt`
- Once those are working successfully, script-ify it with the following parameters:
    - Script is passed the file name as an argument
    - Script prompts the user to to enter one of two options:
        - `E for get emails`
        - `I for get ids`
    - Based on the input, script either:
        - Parses the file for email addresses and saves them to a file called `list-emails.txt`
        - Parses the file for ids and saves them to a file called `list-ids.txt`


## gather.info@myserver.com

- Change your hostname via `/etc/hostname` or `hostnamectl`
    - Edit `/etc/hosts`?

- Run the following commands to get a feel for what they report and how it looks.
    - `hostname` - get the system hostname
    - `df -h \` - get drive space taken by system & user files
    - `uptime` - get statics for how long the system has been running (time since last reboot)
    - `systemctl status ssh` - `systemctl status` gets the status of a given service.  In this case we are peeking at `ssh` but you could think bigger picture, like status of a web server.

Make a backup of the default configuration file (ie. `cp main.cf main.cf.backup`)
Breakdown steps:
    Create mailserver
    Create cronjob that sends an email
    Create (script?) that gathers information
    Create cronjob that sends email with information

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.
