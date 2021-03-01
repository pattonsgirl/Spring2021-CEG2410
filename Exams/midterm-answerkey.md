## Written answer:
1. For the regular expression: `^[A-z]{3}\s\d{3}`  
   Describe what the regular expression can match, then create an example that would and an example that would not match the expression.

   - starts with (^) three letters (`{3}`), capital or lowercase `a-z`
   - followed by a space (`\s`)
   - then three (`{3}`) numbers (`\d`)
   - since there is no `$`, anything can come after
   - Matching example: `Aaa 123`
   - Non-matching example: `123 Aaa`

2. Describe a difference between the POP and IMAP email server protocols.

   - POP clients are going to have individual tracking and updates of emails mail server just pushes email, there is no talk back
   - IMAP clients are synced with what is happening with your mailbox via the mail server 

3. I have an organization using public subnet 12.32.45.0/16.  What is the corresponding subnet mask?

   - 255.255.0.0

4. I have an organization using public subnet 12.32.45.0/16.  They are allowed to share files over SFTP (port 22).  12.32.45.89 is actually a website that should be publicly accessible over port 443.  Discuss some network level (rules for pcs connected or connecting to this subnet) firewall rules you would recommend given this set up.

   - 12.32.45.0/16 should have open SSH (port 22) access - no other networks should have accessibility
   - The world should have access to specifically 12.32.45.89 over port 443.
   - All other ports should be inaccessible since they have not been specified.

5. How can a computer with a private IP address communicate with the outside world?  The role of NAT should be used in your answer.

   - Computers with private IPs need to communicate with the outside world via some sort of routing device that uses NAT (network address translation) to translate the traffic from internal only to a public ip that can communicate with the outside.  If traffic was sent directory from a private IP, it may go out, but return packets would have no way to get back.

6. When running low on disk space, describe something discussed so far that could be deleted / cleaned up.

   - checks logs / temp files
   - old kernels / backups
   - unused packages

## Written commands / code
1. In a local git repository, a new file is created called `spring.txt`  
   Write the steps needed to add the file to a remote repository (GitHub).

   - `git add spring.txt`
   - `git commit -m "shiny new file"`
   - `git push`

2. Write a function called foo that prints the phrase "Howdy!" when called.  
   - both examples can be called with `foo` within the script
```
foo () {
   echo "Howdy!"
}
```
```
function foo {
   echo "Howdy!"
}
```

3. Write a bash if statement that checks to see if the file `groceries` exists with read permissions. If so, print the contents of the file to the terminal.

```
if [[ -r groceries ]]
then
   cat groceries
fi
```
   - partial credit for `-f` or `-e`

4. Craft the necessary command(s) to change the permissions so that `jack` is the owner and has only read and write permissions, `dev` is the group associated with the file and has only write permissions, and others can only read.

```
--wxr-x-wx bob bob file.txt
```

   - Subset of answers:
```
chown jack:dev file.txt
chmod 624 file.txt
```
```
chown jack file.txt
chgrp dev file.txt
chmod 624 file.txt
```
```
chown jack file.txt
chgrp dev file.txt
chmod u=rw,g=w,o=r file.txt
```
```
chown jack file.txt
chgrp dev file.txt
chmod u+rw file.txt
chmod u-x file.txt
chmod g+w file.txt
chmod g-rx file.txt
chmod o+r file.txt
chmod o-wx file.txt
```

5. Write the CIDR notation form of a subnet with a network prefix of 17.158.5.45 and a subnet mask of 255.255.255.0

   - 17.158.5.45/24 and 17.158.5.0/24 

6. `test.sh` contains the following contents.
```
#! /bin/bash
foo () {
    echo $1
}

echo $1
foo bar
```
On the command line, I run the script as follows:
```
test.sh orange banana
```
What is the output of the script?

   - Answer
```
orange
bar
```

7. I have a script to run with a cronjobs.  The path to the script is /usr/bin/my-script  Assume all permission have been set appropriately.  Write a cron entry that will run this script at 7:00 PM on Wednesdays regardless of day of the month or month of the year.

   ` 0 19 * * 3 /usr/bin/my-script`

## Fill in the blank
1. Given a key pair, the ____ key is the key that is added to systems we want to connect to, such as GitHub or the AWS instance we are using.

   - public

2. HTTP is bound to port ____ by default.

   - 80

3. In bash, `for` and `while` loops have their actions for each iteration surrounded by ____ and ____

   - `do` and `done`

4. In bash, I create a variable: `file-count=70`  The value stored by the variable is accessed by using ____

   - `$file-count`

## True / False
1. Commands run with sudo / run as root are run with an EUID of 123.

   - False.  root / sudo assume an EUID of 0

2. In our configuration to send mail from our AWS server, we used Google / Gmail as the SMTP server to send email traffic.

   - True

3. `/etc/hostname` is a file where the hostname for the system can be set.  The hostname should correlate with an IP address listed in `/etc/hosts`

   - True

4. Fail2Ban and mkdir are two example of programs that can scan for suspicious traffic on a Linux system.  Fail2Ban focuses on program / service logs to detect suspicious activity.  mkdir focuses on traffic on the network to detect and correct for DDOS attacks, for example.

   - False.  PSAD, not mkdir