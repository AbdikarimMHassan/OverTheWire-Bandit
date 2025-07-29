# OverTheWire-Bandit
This repository contains  my step-by-step guide to solving the first 20 levels in the **Bandit** Linux game by **Over The Wire** in the OverTheWire wargames.
This repository documents:


The challenges at each level


My solutions


Key takeaways

**Bandit Level 0-1**


**Level Goal**: The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.


- Since you start at the home directory, you can inspect its content using the **ls** command which lists the readme file.
- Use the **cat** command to read the file
- password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If              


**Bandit Level 1-2**

**Level Goal**: The password for the next level is stored in a file called **-** located in the home directory


We know the file is in the home directroy. To read the file, we can use the cat command.  However, file has a name '-' which the cat command treats as standard input from the keyboard and not the name of the file. To indicate that it is the liternal name of the file, use **./** which refer to the current directory and the path seperator. This solves the confusion. so the full command is **cat ./-**
-Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
