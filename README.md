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
- Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

  **Bandit Level 2-3**
**Level Goal**: The password for the next level is stored in a file called –spaces in this filename– located in the home directory

  
I noticed this is similar to the level 1-2 level goal but with spaces in the filename. We used ls to list directory content. There was a file named --spaces in this filename--.
Since the file start with a dash and has spaces. we can do the same solution but with quotes around the full filename.
-Solution: cat ./"--spaces in this filename'
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx



**Bandit Level 3-4**

**Level Goal**: The password for the next level is stored in a hidden file in the inhere directory.


As a standard,  ensure to list all the content of the home directory using the **ls** command. There was a directroy called **inhere**. So we cd'd to that directory: cd inhere/ and used ls to inspects its content and noticed that there was nothing there. I though this was probably becuase the file was a hidden file. So we used the -a option with ls to list all files including hidden. This confirmed there was a hidden file named ...Hiding-From-You. 

- Solution: cat ...Hiding-From-You
- Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ



  **Bandit Level 4-5**

  **Level Goal**: The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Since the file is in the inhere directory, we switched to that directroy using cd inhere/. To list the file type, the command is 'file'. To list all the file type in the directroy, we simply use /* so File /*
The human readabfile file was ./-file07

- Solution: file /* ,  cat ./-file07
- Password:4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

    **Bandit Level 5-6**

  **Level Goal**: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, not executable.


  The file is in the inhere directory, so we simply change to it using cd inhere/. The file has some specific attributes such as 1033 byte size and the best way to search for the file and specify parameters to narrow down the search is using the 'find' command.
  - Solution: To identify the file: find . -type f -size 1033c -not -exectuable. To read file: cat ./maybehere07/.file2
  - Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

 **Bandit Level 6-7**
 **Level Goal**:







  
