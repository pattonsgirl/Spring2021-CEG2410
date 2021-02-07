# Project 3

## Advice & Resources

When writing scripts, there are two ways to go about making sure you're on the right track.  When first learning, I recommend running each command on the command line, then writing it in your script if it worked.  If you've programmed before, you may remember that print statements are your best friend when it comes to debugging.

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

**Resources**
- [Regex101](https://regex101.com/)
    - [Learn RegEx with mini-challenges](https://regexone.com/)
- [`sed` tutorial to manipulate text](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)
- [How to create a cronjob](https://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)
- [Setup ssmtp for mail](https://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)
    - [How to Create and Sign In with App Passwords](https://support.google.com/accounts/answer/185833?hl=en&ctx=ch_DisplayUnlockCaptcha)
- [Send emails via cron](https://www.nixtutor.com/linux/sending-email-alerts-through-cron/)

## [You've got the magic in you](https://www.youtube.com/watch?v=DqMZ8TieXfU&ab_channel=puddles235)

A very common task as a sys admin is dealing with data.  Specifically, data that needs cleaning up in some fashion - ethier by getting out a specific set of info, cleansing bad data, etc.  

- In the main folder of your repository, create a folder called `file-scripts`
- Using `wget` download this file to your folder:
    - https://raw.githubusercontent.com/pattonsgirl/Spring2021-CEG2410/main/Projects/Project3/list.txt
- Use `sed` or another method of your choice to parse out **only the emails** from `list.txt`  Do not overwrite `list.txt`, instead save them to a file called `list-emails.txt`
- Use `sed` or another method of your choice to parse out **only the ids** from `list.txt`  Do not overwrite `list.txt`, instead save them to a file called `list-ids.txt`
- Once those are working successfully, create a script named `parse-data` that will do the following:
    - Script is passed the file name as an argument
    - Script prompts the user to to enter one of two options:
        - `E for get emails`
        - `I for get ids`
        - Note that if else statements are acceptable, so are fancier ways
    - Based on the input, script either:
        - Parses the file for email addresses and saves them to a file called `list-emails.txt`
        - Parses the file for ids and saves them to a file called `list-ids.txt`

**Resources**
- [Regex101](https://regex101.com/)
    - [Learn RegEx with mini-challenges](https://regexone.com/)
- [`sed` tutorial to manipulate text](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)


## gather.info@myserver.com

- Create a file named `email-info.md` in your `server-scripts` folder.  Here is where you will provide documentation for this portion of the project.  Write your documentation such that I can clearly see what steps you took in your solution to each part.  If you don't reach the final goal (sending an email) this will be all you have to argue for partial points.

- Change your hostname:
    - Edit `/etc/hostname` with the hostname you want (this is to replace `ip-10-0-0-20`)
    - Edit `/etc/hosts` - on the first line, add space followed by your hostname
        - `127.0.0.1 localhost new_hostname`
- Run the following commands to get a feel for what they report and how it looks.
    - `hostname` - get the system hostname
    - `uptime` - get statics for how long the system has been running (time since last reboot)
- In your `server-scripts` folder, add the commands above to a script named `system-pulse` and have it output the result of the commands to the terminal.  No fancy redirection, just spit it all out to the terminal.
- Create a `cronjob` that runs `system-pulse` once a day, every day of the week.  Time is up to you.
    - [How to create a cronjob](https://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)
    - Note: while making sure the `cron` is working, I would have set it to a time or repetition where you can quickly see results.
- Configure `ssmtp` on the system so that you can send mail.  [This guide has been confirmed to work](https://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)
    - https://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html
    - Note: for `hostname` in `ssmtp.conf` I used my system hostname that I made.
    - Note: this has only been tested with a gmail account.  I would create a dummy one if you don't have one (or if you don't want to use yours for course work).
    - Authorization note: If you have 2FA setup for your gmail account, you will need to create a secondary password.  [How to Create and Sign In with App Passwords](https://support.google.com/accounts/answer/185833?hl=en&ctx=ch_DisplayUnlockCaptcha)
- Once your email from the system works, change your `cronjob` to [mail you the results of your script](https://www.nixtutor.com/linux/sending-email-alerts-through-cron/)
- Now, drumroll, send me an email from your `cronjob` using my `@wright.edu` address.  To prove who you are:
    - Temporarily modify `system-pulse` to include your name or WSU email

## Git -> GitHub Reminder

Reminder to `add`, `commit` and `push` your wonderful work for grading.

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project you are submitting.
