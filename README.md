# OverTheWire-Bandit Linux Challenge
This repository contains  my step-by-step guide to solving the first 20 levels in the **Bandit** Linux game by **Over The Wire** in the OverTheWire wargames.
This repository documents:


**The challenge at each level**

**My solutions and thought process**




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

 
 **Level Goal**: The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size.
Similar to level 5, this file has some attributes we can use to narrow it down. This already indicated to me we would likely need to use the find command. Since the hint indicates somewhere in the server and not the current directory, we need to use the /. We tried: find / -user bandit7 -group bandit6 -size 33c. But this produced a denied error. To supress this we need to use: 2>/dev/null.

- Solution: find / -user bandit7 -group bandit6 -size 33c 2>/dev/null. cat /var/lib/dbkg/info/bandit7.password
- Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

- 
**Bandit Level 7-8**

  
**Level Goal**: The password for the next level is stored in the file data.txt next to the word millionth

The hint already indicates this is a text search and i was already thinking of the grep command. So as usual we listed the directory content which contained data.txt file. So we simply searched the word millionth within the file using grep command.

- Solution: grep millionth data.txt
- Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

  **Bandit Level 8-9**

  
  **Level Goal**: The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

This hint indicates a sorting and identifying command that eliminates duplicates. So a combination or either of uniq and sort command.

Sort - is line-based and it sorts lines of text in alphabetical order. Since its in alphabetical order, duplicates are next to each other.


Unique - remove duplicates when the duplicates are adjacent. So if the duplicate is directly above or below. If there is something unique in between, it doesn't recognise. Combine with -u  to remove all lines that have adjacent duplicates and doesnt leave any out. 

So we combine with sort for a truly unique line: sort data.txt | unique - u

- Solution:  sort data.txt | unique - u
- Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM


  **Bandit Level 9-10**

**Level Goal**: The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

We used the strings command to extract human-readable text and filtered the result with grep.

- Solution: strings data.txt | grep ===

- Password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

**Bandit Level 10-11**

**Level Goal**: The password for the next level is stored in the file data.txt, which contains base64 encoded data.

The data was base64 encoded, so we decoded it using the base64 command with the -d option.

- Solution: base64 -d data.txt

- Password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

**Bandit Level 11-12**

**Level Goal**: The password for the next level is stored in the file data.txt, where all lowercase and uppercase letters have been rotated by 13 positions.

This is a ROT13 cipher. We used the tr command to rotate the letters.

- Solution: cat data.txt | tr A-Za-z N-ZA-Mn-za-m

- Password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

**Bandit Level 12-13**

**Level Goal**: The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.

We created a working directory in /tmp, reversed the hex with xxd -r, and used file to identify compression types. Then, we used a combination of mv, gunzip, bunzip2, and tar to repeatedly decompress the file.

**Solution:** Followed multiple decompression steps using xxd, gunzip, bunzip2, and tar

- Password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

- Bandit Level 13-14

- Level Goal: The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14.

We were given a private SSH key to log in as bandit14.

- Solution: ssh -i sshkey.private bandit14@localhost

- Password: (accessed in session, not printed)

**Bandit Level 14-15**

**Level Goal**: The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

We used telnet to connect to the port and entered the current level's password.

- Solution: telnet localhost 30000, then input 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

- Password: BfMYroe26WYalil77FoDi9qh59eK5xNr

**Bandit Level 15-16**

**Level Goal:** The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

We used the openssl s_client command to communicate with the SSL port and entered the password.

- Solution: openssl s_client -connect localhost:30001, then input BfMYroe26WYalil77FoDi9qh59eK5xNr

- Password: cluFn7wTiGryunymYOu4RcffSxQluehd

**Bandit Level 16-17**

**Level Goal**: The credentials for the next level can be retrieved by submitting the password to a port between 31000 and 32000. Only one server will return the next credentials.

We used nmap to find open ports, then tested each one with openssl s_client. One of them returned a private key, which we saved, gave permissions, and used to login.

- Solution:

nmap -p 31000-32000 localhost

openssl s_client -connect localhost:<correct_port>

chmod 400 keyfile

ssh -i keyfile bandit17@localhost

- Password: (accessed after login)

**Bandit Level 17-18**

**Level Goal**: The password for the next level is in passwords.new and is the only line that differs from passwords.old.

We used the diff command to compare both files and extract the changed line.

- Solution: diff passwords.old passwords.new

- Password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

**Bandit Level 18-19**

- Level Goal: The password is stored in a readme file in the home directory, but .bashrc logs you out immediately after login.

We bypassed the login script by forcing a shell using the -t /bin/sh option.

- Solution: ssh bandit18@bandit.labs.overthewire.org -p 2220 -t /bin/sh, then cat readme

- Password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

**Bandit Level 19-20**

**Level Goal**: A setuid binary is in the home directory. Run it to access the password for the next level.

We used the setuid binary to act as bandit20 and read the password file.

- Solution: ./bandit20-do cat /etc/bandit_pass/bandit20

- Password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j


  

 







  
