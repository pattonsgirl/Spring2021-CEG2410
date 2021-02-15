# Quiz 2

1. cron job with settings:
`45 10 * * * /home/ubuntu/bubbles`
When does the script run?

- 10:45 in the morning, every day of the month, every month of the year, every day of the week.

2. What command will let you download a file, provided the URL of a file to download?

- `wget`

3. After running a command, I am getting this error:
`cat: bubbles.txt: No such file or directory`
What is the problem and what is a solution?

- The file `bubbles.txt` does not exists in the directory.  
- Create `bubbles.txt`
- Move to the correct folder

4. ____ runs when we first log in to a Linux system for the day and by default prints a message that contains details on the system, details about updates, and links to helpful articles and noteworthy news

- MOTD, Message of the Day

5. Given the line of text in the file line.txt:
"Marn, Anel", marnanel@yahoo.com, 84390
Write a regular expression pattern that will match the email address only.

- Mine: \w+@\w+\.\w+
- marnanel@yahoo.com
- /([a-zA-Z0-9._-]+@[a-zA-Z0-9._-]+\.[a-zA-Z0-9_-]+)/
- Wrong:
    - ^\S{1,}@\S{2,}\.\S{2,}$
