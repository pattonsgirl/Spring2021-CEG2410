# Project 2

## Kick Off

- Click link to join Linux GitHub Classroom
- Clone your repository to your AWS Linux / Ubuntu instance
  - Make sure you have created a key in the Ubuntu machine and uploaded the public key to GitHub
  - [Create a key pair, upload public key to github](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
  - [Change your repo to authenticate with SSH (not HTTPS)](https://haydar-ai.medium.com/learning-how-to-git-using-ssh-instead-of-https-91f09cff72de)
  - [If errors poke around here](https://docs.github.com/en/github/authenticating-to-github/error-permission-denied-publickey)

## Advice & Resources

When writing scripts, there are two ways to go about making sure you're on the right track.  When first learning, I recommend running each command on the command line, then writing it in your script if it worked.  If you've programmed before, you may remember that print statements are your best friend when it comes to debugging.

Remember that Google is your friend - its pretty rare as a sys admin to run in to a problem that no one else has ever found.  Between forums, blogs, and **documentation** you can usually find an answer or a place to start.  If you feel like you are going down a "rabbit hole" ask questions on the Discord channel so I or your classmates can push you back in the right direction.

- [Ubuntu 16 MOTD](https://oitibs.com/ubuntu-16-04-dynamic-motd/)
- [Vim Jellybeans GitHub Page](https://github.com/nanotech/jellybeans.vim)

### Just the way you like it

The goal here is to write a script just for you.  This script is something you can run as long as you are on a Linux system (with bash installed).  

- In the main folder of your repository, create a folder called `user-scripts`
- Create a new script file named `my-way`
- Have your script output a statement about what it does.
  - `This script will ...` where ... is what your script does.
- Run the script with `source my-way` or set the `execute` permission on my way so you can use `./my-way`
- Your first objective is to download a file from the internet to a specific spot.  The file to download is: 
  - `https://raw.githubusercontent.com/nanotech/jellybeans.vim/master/colors/jellybeans.vim`
  - Download the file (or move the file) to `~/.vim/colors/`
    - Note: in your terminal while you fidget **and** in your script, you will need to make this directory
  - Commands to play with: `curl`, `wget`
  - Get this down to using one line / command
  - Once you have it as one line that downloads the file & puts it in the directory specified, add the line to your script.
- Your second objective is to "enable" it.  What you have downloaded is a coloring configuration for `vim`
  - The `vim` program looks at `~/.vimrc` for what configurations to enable.
  - Add the line `colorscheme jellybeans` to `~/.vimrc`
  - Make this happen via redirection.  Useful commands: `echo`, `>`, `>>`
  - Once you have it as one line that puts text in `~/.vimrc`, add the line to your script.
- Have your script prompt the user to see if they want `jellybeans for vim` installed.
  - If they respond with `y` for yes, then run your two commands (download the file & enable it in `~/.vimrc`) then print `Good to go!  Please run vim on a file`
  - Else print out `Okay, Bye!`

### sudo show me what I want to see

Sometimes your script can only work if it is run as root.  Think needs to run as admin.

- In the main folder of your repository, create a folder called `server-scripts`
- Create a new script file named `mod-motd`
- Write a print statement that will **only** print if the script is run as `sudo` or as `root`
  - Else print `You are not the admin I am looking for`
- Write a function called `installs`
  - In this function, write statement(s) to install `htop`, `python3`, `python3-pip`, `ack`
  - Call the function from your `if` sudo statement
- Write a function called `motd-message`
  - The message of the day is a message that displays when you first log in.  You may have noted that it contains an amount of junk (news channels, etc.)  The message of the day is actually a series of files in `/etc/update-motd.d/`
  - Look through these files (using `cat`) to figure out which display useful info and which display fluff. (Note: this is not part of your final script)
    - "Fluff", to me, is links to the support pages and news updates.  Security updates, versions, and last log in is all more useful info.
  - Rename the "fluff" files to old-originalname
  - Call the function from your `if` sudo statement


## Submission

In your GitHub repository, select the green `Code` button then select `Download ZIP`. Upload this zip file to Pilot.

In the `Comment` area in the Pilot Dropbox, copy URL / link to the repository corresponding to the project your are submitting.
