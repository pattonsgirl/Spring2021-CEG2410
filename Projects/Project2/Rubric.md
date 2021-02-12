# Project 2 Rubric

 / 12

## Connected to GitHub Classroom repo - / 2

## vim script - / 6
- Script `my-way` in `user-scripts` folder
    - downloads jellybeans
    - jellybeans is placed in correct directory - `~/.vim/colors`
    - uses output redirection to add `colorscheme jellybeans` to `~/.vimrc`
    - prompts user for input
    - only downloads & adds text if user entered y or yes
    - else prints exit message

## motd & installs  script - / 4
- Script `mod-motd` in `server-scripts` folder
    - script checks permissions (EUID recommended)
    - `installs` function
        - installs package list
    - `motd-message` function
        - renames a file in `/etc/update-motd/`
    - script only runs `installs` and `motd-message` if root permissions are given