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
- Using `wget` download these two files:
    - 

## gather.info@myserver.com

Set up mail server on the AWS system, have it use a cron job that emails system stats every so often

Stats:
    hostname
    drive space
    Uptime
    CPU 
    SSH health?

Breakdown steps:
    Create mailserver
    Create cronjob that sends an email
    Create (script?) that gathers information
    Create cronjob that sends email with information

## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.
