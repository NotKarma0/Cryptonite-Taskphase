

# 1. Hello Hackers

## Intro to commands
In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:

### Solve
**Flag:** `pwn.college{0A-buwr6cYY7R__wLw0nmbzsyUR.QX3YjM1wCMxYzNyEzW}`

I typed hello.

```bash
hello 
pwn.college{0A-buwr6cYY7R__wLw0nmbzsyUR.QX3YjM1wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## Intro to arguments
Let's try something more complicated: a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments. The first word is the command, and the subsequent words are arguments. Observe:

### Solve
**Flag:** `pwn.college{gYI0dmmeqojxCLONFDuPA-AnJAD.QX4YjM1wCMxYzNyEzW}`

I typed hello hackers

```bash
hello hackers
pwn.college{gYI0dmmeqojxCLONFDuPA-AnJAD.QX4YjM1wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## Command History
You're going to type a lot of commands, and typing everything from scratch can be annoying. Luckily, the shell saves a history of every command you invoke.

### Solve
**Flag:** `pwn.college{UOEt14J18KLbIkeA_3RKFj4QpIo.0lNzEzNxwCMxYzNyEzW}`

I hit the up arrow.

```bash
pwn.college{UOEt14J18KLbIkeA_3RKFj4QpIo.0lNzEzNxwCMxYzNyEzW}
```

### New Learnings
None

### References 
None

# 2. Pondering Paths

## The Root
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

### Solve
**Flag:** `pwn.college{ghWQHQKQXxXMl0EiwvgqlRdvF6v.QX4cTO0wCMxYzNyEzW}`

type in your solve and your thought process behind solving the challenge. Include as much as info as possible. Use triple ticks for any bash commands and output you type on the terminal.

```bash
/pwd
pwn.college{ghWQHQKQXxXMl0EiwvgqlRdvF6v.QX4cTO0wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## Program and absolute paths
ALet's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

### Solve
**Flag:** `pwn.college{gaofGDfX_H3uaNcQM5Ud0lk_Dt1.QX1QTN0wCMxYzNyEzW}`

Honestly this confused me. I did cd, pwd to check my current location. And then did a lot of stuff found a file named flag which denied me permissions to open the file. But then i did /challenge/run and it worked.

```bash
/challenge/run
pwn.college{gaofGDfX_H3uaNcQM5Ud0lk_Dt1.QX1QTN0wCMxYzNyEzW}
```

### New Learnings
Dont think too much

### References 
None

## Position thy self
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

### Solve
**Flag:** `pwn.college{YjwFI6AfM0dLepvz7qHBCWsG9Y_.QX2QTN0wCMxYzNyEzW}`

At first i did /challenge/run. It said incorrect and that i need to be in in /var/log directory so i went to that directory and ran the program

```bash
hacker@paths~position-thy-self:/home$ /challenge/run
Incorrect...
You are not currently in the /var/log directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/home$ cd /var/log
hacker@paths~position-thy-self:/var/log$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{YjwFI6AfM0dLepvz7qHBCWsG9Y_.QX2QTN0wCMxYzNyEzW}
hacker@paths~position-thy-self:/var/log$ 
```

### New Learnings
None

### References 
None

## Position elsewhere
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

### Solve
**Flag:** `pwn.college{0pamLLG6Bo_3vV-QgL0hXXkeZpJ.QX3QTN0wCMxYzNyEzW}`

I did the same thing I did in the last challenge.

```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{0pamLLG6Bo_3vV-QgL0hXXkeZpJ.QX3QTN0wCMxYzNyEzW}
hacker@paths~position-elsewhere:/usr/share/zoneinfo/posix/Asia$ 
```

### New Learnings
None

### References 
None

## Position yet elsewhere
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

### Solve
**Flag:** `ppwn.college{4CO5bEIRL71-mCTVv9zxF7GODaN.QX4QTN0wCMxYzNyEzW}`

Same thing as last time.

```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /tmp directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /tmp
hacker@paths~position-yet-elsewhere:/tmp$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4CO5bEIRL71-mCTVv9zxF7GODaN.QX4QTN0wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## Implicit relative paths, from /
Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊

### Solve
**Flag:** `pwn.college{IKk3l6sZN9NLyyweN3RjwdAO5cr.QX5QTN0wCMxYzNyEzW}`

Well i tried some stuff, then I was was told to access relative path not an absolute path. And when i did so i got the flag.

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ /challenge/run
Incorrect...
You invoked this challenge with an absolute path. This challenge needs a relative path!
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{IKk3l6sZN9NLyyweN3RjwdAO5cr.QX5QTN0wCMxYzNyEzW}

```

### New Learnings
None

### References 
None

## explicit relatives path, from /
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using . in your relative paths. Get ready!

### Solve
**Flag:** `pwn.college{M_tFB4cVDMWQVwJB-1ibu17G7a9.QXwUTN0wCMxYzNyEzW}`

Yeah same thing basically. But i learned the other ways of calling relative paths.

```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ challenge
bash: challenge: command not found
hacker@paths~explicit-relative-paths-from-:/$ challenge/
bash: challenge/: Is a directory
hacker@paths~explicit-relative-paths-from-:/$ challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{M_tFB4cVDMWQVwJB-1ibu17G7a9.QXwUTN0wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## implicit relative path
We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!

### Solve
**Flag:** `pwn.college{gQl_iiG-2jg2Xy9u4AI53pGo7P4.QXxUTN0wCMxYzNyEzW}`

I did ./run to execute the program.

```bash
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gQl_iiG-2jg2Xy9u4AI53pGo7P4.QXxUTN0wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## home sweet home
Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
Again, you must specify your path as an argument to /challenge/run as so: 

### Solve
**Flag:** `pwn.college{UqkG_GAnPijTXWitMAPg9la0K7t.QXzMDO0wCMxYzNyEzW}`

I tried many things. I understood that the your path name must be only 3 characters in here for copying the file. So what i did inititally was try doing /challenge/run ~ and it didnt work. So when i kept looking at the question they created a file using ~/asdf. So when i tried doing it it worked.

```bash
hacker@paths~home-sweet-home:~$ /challenge/run ~/asdf
The argument you provided must not have been longer than 3 characters (it's 
currently 6 characters long)!
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{UqkG_GAnPijTXWitMAPg9la0K7t.QXzMDO0wCMxYzNyEzW}
```

### New Learnings
I learnt how to make a copy of the program to the file.

### References 
None

# 3. Comprehending Commands

## cat: not the pet, but the command!
Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!

### Solve
**Flag:** 'pwn.college{8y1_pe8WeA1yPp_g6BJLCpPWGRk.QXxcTN0wCMxYzNyEzW}'
I typed cat flag.

```bash
hacker@commands~cat-not-the-pet-but-the-command:/$ cat flag
pwn.college{8y1_pe8WeA1yPp_g6BJLCpPWGRk.QXxcTN0wCMxYzNyEzW}
```

### New Learnings
None

### References 
None

## cat absolute paths
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.

### Solve
**Flag:** 'pwn.college{Uyi2cJE6MAXA1-9fJZile96jbqm.QX5ETO0wCMxYzNyEzW}'

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{Uyi2cJE6MAXA1-9fJZile96jbqm.QX5ETO0wCMxYzNyEzW}
```
### New Learning
None

### References
None

## more catting practice
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.

### Solve
**Flag:** 'pwn.college{8UKcC8BdjPSI68kJaeb99bGZ_cp.QXwITO0wCMxYzNyEzW}'

```bash
hacker@commands~more-catting-practice:~$ cat /lib/x86_64-linux-gnu/perl-base/flag
pwn.college{8UKcC8BdjPSI68kJaeb99bGZ_cp.QXwITO0wCMxYzNyEzW}
```

### New Learning
None

### References
None

## grepping for a needle in a haystack
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

HINT: The flag always starts with the text pwn.college.

### Solve
**Flag:** 'pwn.college{0XNOF4iCnyHZ_k7plA7pX8slhv_.QX3EDO0wCMxYzNyEzW}'

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{0XNOF4iCnyHZ_k7plA7pX8slhv_.QX3EDO0wCMxYzNyEzW}
```

### New Learning
grep finds a text to search in a big paragraph or stuff.

### References
None

## comparing files
This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add line 2 of file2").

Now for your challenge! There are two files in /challenge:

/challenge/decoys_only.txt contains 100 fake flags
/challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!

### Solve
**Flag:** 'pwn.college{cwqpVghH0EhVON1HRKLFZjZxDpE.01MwMDOxwCMxYzNyEzW}'

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
97a98
> pwn.college{cwqpVghH0EhVON1HRKLFZjZxDpE.01MwMDOxwCMxYzNyEzW}
```

### New Learning
diff gets the difference between two files.

### References
None

## listing files
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.

### Solve
**Flag:** 'pwn.college{wFj9KzXMy12t6PBuOem_aYln0O-.QX4IDO0wCMxYzNyEzW}'

```bash
hacker@commands~listing-files:/challenge$ ls /challenge
15590-renamed-run-18885  DESCRIPTION.md
hacker@commands~listing-files:/challenge$ cat 15590-renamed-run-18885
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:/challenge$ cat /flag
cat: /flag: Permission denied
hacker@commands~listing-files:/challenge$ ./15590-renamed-run-18885
Yahaha, you found me! Here is your flag:
pwn.college{wFj9KzXMy12t6PBuOem_aYln0O-.QX4IDO0wCMxYzNyEzW}
```

### New Learning
None

### References
None

## touching files
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!

### Solve
**Flag:** 'pwn.college{YUeLfTwS2CNCGIva-txLLloCzI2.QXwMDO0wCMxYzNyEzW}'

```bash
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{YUeLfTwS2CNCGIva-txLLloCzI2.QXwMDO0wCMxYzNyEzW}
```

## removing files
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!

### Solve
**Flag:** 'pwn.college{8VNExJLIJzhIIS95hssh2RyPJGj.QX2kDM1wCMxYzNyEzW}'

```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{8VNExJLIJzhIIS95hssh2RyPJGj.QX2kDM1wCMxYzNyEzW}
```

### New Learning
None

### References
None

## moving files
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.

### Solve
**Flag:** 'pwn.college{sPMnefM4T1LUfM7-JxFVgptBgcA.0VOxEzNxwCMxYzNyEzW}'

```bash
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{sPMnefM4T1LUfM7-JxFVgptBgcA.0VOxEzNxwCMxYzNyEzW}
```

### New Learning
None

### References
None

## copying files
But what if you want to keep the original file? You can do so with the cp command. The usage is the same as with mv, but it will keep the source file.

This challenge wants you to copy the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.

### Solve
**Flag:** 'pwn.college{IohBrt_d_uayZdWcea6L1DUnsxI.0lNxQTMywCMxYzNyEzW}'

```bash
hacker@commands~copying-files:~$ cp /flag /tmp/hack-the-planet
Correct! Performing 'cp /flag /tmp/hack-the-planet'.
hacker@commands~copying-files:~$ /challenge/check
Congrats! You successfully copied the flag to /tmp/hack-the-planet! Here it is:
pwn.college{IohBrt_d_uayZdWcea6L1DUnsxI.0lNxQTMywCMxYzNyEzW}
```

### New Learning
None

### References
None

## hidden files
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.

### Solve
**Flag:** 'pwn.college{EzWBU6lwNVNkLc5MX7h6b0koUBA.QXwUDO0wCMxYzNyEzW}'

```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-22261324728176  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat flag-22261324728176
cat: flag-22261324728176: No such file or directory
hacker@commands~hidden-files:/$ ls flag-22261324728176
ls: cannot access 'flag-22261324728176': No such file or directory
hacker@commands~hidden-files:/$ cat .flag-22261324728176
pwn.college{EzWBU6lwNVNkLc5MX7h6b0koUBA.QXwUDO0wCMxYzNyEzW}
```

### New Learning
None

### References
None

## An Epic Filesystem Quest
In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!

### Solve
**Flag:** 'pwn.college{I87LXvbxdRmmrRSbVdrlUJlNg36.QX5IDO0wCMxYzNyEzW}'

```bash
too many commands
```

### New Learning
None

### References
None

## making directories
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!

### Solve
**Flag:** 'pwn.college{46SfYExHwUKNsA9rKZUPxZU3djP.QXxMDO0wCMxYzNyEzW}'

```bash
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{46SfYExHwUKNsA9rKZUPxZU3djP.QXxMDO0wCMxYzNyEzW}
```

### New Learning
None

### References
None

## finding files
Now it's your turn. I've hidden the flag in a random directory on the filesystem. It's still called flag. Go find it!

Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it. Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there! Finally, find can take a while; be patient!

### Solve
**Flag:** 'pwn.college{MrCemwEEPvcrYesDvLgCava-OXV.QXyMDO0wCMxYzNyEzW}'

```bash
find / -name flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/lib/debug/.build-id/6c/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
cat /usr/lib/debug/.build-id/6c/flag
pwn.college{MrCemwEEPvcrYesDvLgCava-OXV.QXyMDO0wCMxYzNyEzW}
```

### New Learning
How to use find command.

### References
None

## linking files 
Okay, now you try it! In this level the flag is, as always, in /flag, but /challenge/catflag will instead read out /home/hacker/not-the-flag. Use the symlink, and fool it into giving you the flag!

### Solve
**Flag:** 'pwn.college{UgmAdVQ7b-6iHqpFhaHdO0B5aom.QX5ETN1wCMxYzNyEzW}'

```bash
hacker@commands~linking-files:~$ cat /flag
cat: /flag: Permission denied
hacker@commands~linking-files:~$ cat /challenge/catflag
#!/opt/pwn.college/bash
fold -s <<< "About to read out the /home/hacker/not-the-flag file!"
cat /home/hacker/not-the-flag
hacker@commands~linking-files:~$ cat /home/hacker/not-the-flag
cat: /home/hacker/not-the-flag: No such file or directory
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{UgmAdVQ7b-6iHqpFhaHdO0B5aom.QX5ETN1wCMxYzNyEzW}
```

### New Learning 
Hose to link files.

### References
None

# 4. Digesting Documentation
## Learning from documentation
The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

Given that knowledge, go get the flag!

### Solve
**Flag:** 'pwn.college{g8rp7Le6FwEj5MYUfoqpm3iNfqb.QX0ITO0wCMxYzNyEzW}'

```bash
hacker@man~learning-from-documentation:~$ ls -l
total 8
-rw-r--r-- 1 root   hacker 60 Nov  4 08:48 a
lrwxrwxrwx 1 hacker hacker  5 Nov 13 10:44 not-the-flag -> /flag
hacker@man~learning-from-documentation:~$ ls -a
.  ..  .bash_history  .cache  .config  .local  a  not-the-flag
hacker@man~learning-from-documentation:~$ cat /flag
cat: /flag: Permission denied
hacker@man~learning-from-documentation:~$ /not-the-flag
bash: /not-the-flag: No such file or directory
hacker@man~learning-from-documentation:~$ ln -s /flag /challenge/challenge
ln: failed to create symbolic link '/challenge/challenge': File exists
hacker@man~learning-from-documentation:~$ /challenge/challenge
Incorrect usage! You must pass an argument to me (read the challenge 
description for details).
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{g8rp7Le6FwEj5MYUfoqpm3iNfqb.QX0ITO0wCMxYzNyEzW}
```

### New Learning 
How to pass by an argument.

### References
None

## Learning complex usage
Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!

### Solve
**Flag:** 'pwn.college{szm3YtXRdyx2aPYPTW0LzLhyUYO.QX1ITO0wCMxYzNyEzW}'

```bash
hacker@man~learning-complex-usage:~$ cat /not-the-flag
cat: /not-the-flag: No such file or directory
hacker@man~learning-complex-usage:~$ cat /flag
cat: /flag: Permission denied
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{szm3YtXRdyx2aPYPTW0LzLhyUYO.QX1ITO0wCMxYzNyEzW}
```

### New Learning 
Learned how to give pass by argument to pass by argument.

### References
None

## Reading manuals
Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!


### Solve
**Flag:** 'pwn.college{MHjzQndPsF1YWAS_AW1IGtV6ypM.QX0EDO0wCMxYzNyEzW}'

```bash
man challenge
/challenge/challenge --jzndst 116
Correct usage! Your flag: pwn.college{MHjzQndPsF1YWAS_AW1IGtV6ypM.QX0EDO0wCMxYzNyEzW}
```

### New Learning 
What is a man file.

### References
None

## Searching manuals
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.

### Solve
**Flag:** 'pwn.college{MglWuH3HZmNuGQfknt4KA-mvU6H.QX1EDO0wCMxYzNyEzW}'

```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --ccvibx
Initializing...
Incorrect usage! Please read the challenge man page!
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --ccivbx
Initializing...
Correct usage! Your flag: pwn.college{MglWuH3HZmNuGQfknt4KA-mvU6H.QX1EDO0wCMxYzNyEzW}
```

### New Learning 
How to search in a man file using /.

### References
None

## Searching for manuals
HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!

### Solve
**Flag:** 'pwn.college{ofOlZNA1YGo3scM7dWQmE6dmYdY.QX2EDO0wCMxYzNyEzW}'

```bash
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man /challenge/challenge
hacker@man~searching-for-manuals:~$ man --oflosc 137
man: unrecognized option '--oflosc'
Try 'man --help' or 'man --usage' for more information.
hacker@man~searching-for-manuals:~$ /challenge/challenge --oflosc 137
Correct usage! Your flag: pwn.college{ofOlZNA1YGo3scM7dWQmE6dmYdY.QX2EDO0wCMxYzNyEzW}
```

### New Learning 
Idk, still in doubt.

### References
Chatgpt.

## Helpful programs
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!

### Solve
**Flag:** 'pwn.college{kJq3mqbsVtRqKabqpNdLDEthmOk.QX3IDO0wCMxYzNyEzW}'

```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -h
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -g GIVE_THE_FLAG
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 330
hacker@man~helpful-programs:~$ /challenge/challenge -g GIVE_THE_FLAG 330
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge -g 330
Correct usage! Your flag: pwn.college{kJq3mqbsVtRqKabqpNdLDEthmOk.QX3IDO0wCMxYzNyEzW}
```

### New Learning 
Help command --help, help, -h, -?, help, /?

### References
None

## Help for builitins
Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!

### Solve
**Flag:** 'pwn.college{wrxDkbuKMp7YyJ67r0hssluj47T.QX0ETO0wCMxYzNyEzW}'


```bash
hacker@man~help-for-builtins:~$ help challenge
hacker@man~help-for-builtins:~$ /challenge --secret wrxDkbuK
bash: /challenge: Is a directory
hacker@man~help-for-builtins:~$ ./challenge --secret wrxDkbuK
bash: ./challenge: No such file or directory
hacker@man~help-for-builtins:~$ challenge --secret wrxDkbuK
Correct! Here is your flag!
pwn.college{wrxDkbuKMp7YyJ67r0hssluj47T.QX0ETO0wCMxYzNyEzW}
```

### New learning
None

### References
None

# 5. File Globbing

## Matching with *
This challenge wants us to change the directory using the glob '*'.

### My solution
**Flag** `pwn.college{wxEymvnerKn7rtajD6Byxc8B3mW.QXxIDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{wxEymvnerKn7rtajD6Byxc8B3mW.QXxIDO0wSNxEzNzEzW}
```

### What I learned 
- This is invalid
'''
hacker@globbing~matching-with-:~$ cd /*l*
bash: cd: too many arguments
hacker@globbing~matching-with-:~$ cd /*e
bash: cd: too many arguments
'''
- To be able to use the glob '*', we have to use the command 'cd /c*'
- This is because, the error means the wildcard created a list of too many places to go and couldn't choose one.

### References
`

## Matching with ?
This challenge wants us to pass the argument of --giveflag to /challenge/challenge to get the flag.

### My solution
**Flag** `pwn.college{kGJocmDdvknmTqvR0AyFBLuR2bO.QXyIDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kGJocmDdvknmTqvR0AyFBLuR2bO.QXyIDO0wSNxEzNzEzW}
```

### What I learned 
- The glob '?' unlike '*' replaces just one character.


## Matching with []
This challenge wants us to search for file_b, file_a, file_s, and file_h using the glob '[]'.

### My solution
**Flag** `pwn.college{Q_GKPlKAttKBNpZDPAzInOGUTsq.QXzIDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{Q_GKPlKAttKBNpZDPAzInOGUTsq.QXzIDO0wSNxEzNzEzW}
```

### What I learned 
- The glob '[]' is a wildcard for some subset of potential characters, specified within the brackets.

### References 
-


## Matching paths with []
This challenge wants us to search for file_b, file_a, file_s, and file_h using the entire paths with the glob '[]'.

### My solution
**Flag** `pwn.college{EwSTXkjV4PnHozPROougaU9HMA9.QX0IDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{EwSTXkjV4PnHozPROougaU9HMA9.QX0IDO0wSNxEzNzEzW}
```
### What I learned 
- The glob '[]' can take a single argument including the absolute paths of the file. 

### References 
-


##Multiple Globs
This challenge wants us to search for all the files that contain the letter p in their name.

## My solution
**Flag** `pwn.college{cy91mu9KTgH6MdvhUIKemtEhhun.0lM3kjNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{cy91mu9KTgH6MdvhUIKemtEhhun.0lM3kjNxwSNxEzNzEzW}
```

### What I learned 
- we can use more than one globs in a single statement.


## Mixing Globs
This challenge wants us to use a 6 or less character glob that will match the files "challenging", "educational".

### My solution
**Flag** `pwn.college{cel6HqAoayiuRTAUY60X0Qjb3l4.QX1IDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cpe]*
You got it! Here is your flag!
pwn.college{cel6HqAoayiuRTAUY60X0Qjb3l4.QX1IDO0wSNxEzNzEzW}
```

### What I learned 
- To use multiple globs together.

### My mistakes
- Earlier I was trying to use the '*' inside the glob '[]'

```bash
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [i*n*]
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
[i*n*]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [*i*n*]
Error: your argument is too long! It must be 6 characters or less.
- The argument '*i*n*' should've worked, but since we're told to use square brackets glob, it doesn't work.
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *i*n*
Error: you did not use a square bracket glob...
```

### References 
-

## Exclusionary Globbing
This challenge wants us to list all files that don't start with p, w, or n using '!'.

### My solution
**Flag** `pwn.college{0dmy6e-pDjn59OqeoU3EOI7qj48.QX2IDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{0dmy6e-pDjn59OqeoU3EOI7qj48.QX2IDO0wSNxEzNzEzW}
```

### What I learned 
- If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. 

### References 
-

## Tab Completion
This challenge wants us to use tab-completion to read the flag.

### My solution
**Flag** `pwn.college{UkRMrqkDZoHZ8M142AodJuNkLVi.0FN0EzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege?
pwn.college{UkRMrqkDZoHZ8M142AodJuNkLVi.0FN0EzNxwSNxEzNzEzW}
```

### What I learned 
- The tab button can be used to autofill the path of the file.


## Multiple options for tab completion 
This challenge requires us to use tab to complete commands for the suggested ones by the terminal.

### My solution
**Flag**  `pwn.college{4LxfmAfH10NHW_oea5B7waSVClb.0lN0EzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/
cat: /challenge/files/: Is a directory
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{4LxfmAfH10NHW_oea5B7waSVClb.0lN0EzNxwSNxEzNzEzW}
```

### What i learned 
The challenge taught me on how to use the tab to complete the commands to get through them easier.

## Tab Completion on Commands
This challenge wants us to use tab-completion to read the flag.

### My solution
**Flag** `pwn.college{g8OnfGT5hUXZIQcaNwuM1Qxe-40.0VN0EzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
Connected!
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-29513
Correct! Here is your flag:
pwn.college{g8OnfGT5hUXZIQcaNwuM1Qxe-40.0VN0EzNxwSNxEzNzEzW}
```
### What I learned 
- The tab button can also be used to complete commands

# 6. Practicing piping 

## Redirecting Output 
This challenge required the use of `>` to redirect the output.

### My solve
**Flag** `pwn.college{Ar-n8GzsVNE191F4LYZ3hwbpqKL.QX0YTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{Ar-n8GzsVNE191F4LYZ3hwbpqKL.QX0YTN0wSNxEzNzEzW}
```

### What I learned
1. I learnt the use of the `>` command to redirect the output to a particular file.


## Redirecting More output
In this challenge i had to redirect the output of the command `/challenge/run`.

### My solve
**Flag** `pwn.college{IbLDrjyl6T1WpeIu6L4N0GAS1XU.QX1YTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{IbLDrjyl6T1WpeIu6L4N0GAS1XU.QX1YTN0wSNxEzNzEzW}
```

### What i learned 
1. I learned how to redirect the output to find the flag from the `my flag` file.


## Appending output 
This challenges uses the `>>` option to redirect files to genrerate the output.

### My solve
**Flag** `pwn.college{wCXq1Ksaa0V-cpd5KDzvlrIgjbv.QX3ATO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat  /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{wCXq1Ksaa0V-cpd5KDzvlrIgjbv.QX3ATO0wSNxEzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
hacker@piping~appending-output:~$
```

### What i learned 
1. I learned the use of the append mode `>>` which redirects the output of the file to another file. 

**Note**
If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag.


## Redirecting errors 
The challenge required to redirect an error just like a file is redirected. 

### My solution 
**My flag** `pwn.college{ccRHAjHWD9Z-FlQI9GkF8rq9ceP.QX3YTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ccRHAjHWD9Z-FlQI9GkF8rq9ceP.QX3YTN0wSNxEzNzEzW}
```

### What i learned 
1. Just like standard output, we can also redirect the error channel of commands.

2. When we redirect a process communication, we do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output)



## Redirecting Input 
This challenge uses `<` to redirect input to programs.

### My solution 
**My flag** `pwn.college{o_eOLNBSAabUdYkiFKtEyUvUtYP.QXwcTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~redirecting-input:~$ /challenge/run > PWN
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{o_eOLNBSAabUdYkiFKtEyUvUtYP.QXwcTN0wSNxEzNzEzW}
```

### What i learned 
1. Using the `<` command we can redirect input into the commands. 


## Grepping stored results 
This challenges conprises of redirecting the files and then using the  `grep` command to search for the resulting file.

### My solution 
**Flag** `pwn.college{YjCPrs3cMtFA2pkkE4KzZ5G-u3e.QX4EDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep "pwn.college" /tmp/data.txt
pwn.college{YjCPrs3cMtFA2pkkE4KzZ5G-u3e.QX4EDO0wSNxEzNzEzW}
```

### What i learned 
Using the `grep` command to search throught the resulting files once the output is redirected.


## Grepping live output 
This challenge uses the `|` operator. 

### My solution 
**Flag** `pwn.college{IDABGfC6hHu3BTDxt2V3TXmW4-n.QX5EDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
[FLAG] Here is your flag:
camouflaged
camouflages
flagellating
flagstone
flagstaff's
flagstone's
persiflage
conflagration
flagging
flagellation's
flagged
flagons
flagrantly
flag
persiflage's
flagstaff
flagstones
flagellated
flagon
flagon's
flagship
camouflaging
unflagging
flagpole's
flagship's
flagella
conflagration's
flagstaffs
flags
flagpole
camouflage
flagellate
flag's
flagellation
flagellum
flagellum's
conflagrations
camouflage's
flagrant
flagships
flagpoles
flagellates
flagellums
hacker@piping~grepping-live-output:~$ /challenge/run | grep "pwn.college"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{IDABGfC6hHu3BTDxt2V3TXmW4-n.QX5EDO0wSNxEzNzEzW}
```

### What i learned 
We can cut out the middleman and avoid the need to store results to a file. We can do this by using the `|` (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe.


### Grepping errors
In this challenge we grep through errors directly. 

### My solution
**Flag** `pwn.college{8SeG84t3ol1Ks9_G8XV3oSAv_fX.QX1ATO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~grepping-errors:~$ 2>& 1
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep "pwn.c
ollege"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8SeG84t3ol1Ks9_G8XV3oSAv_fX.QX1ATO0wSNxEzNzEzW}
```

### What i learned 
1. I learnt how to the shell has a `>&` operator, which redirects a file descriptor to another file descriptor.

## Filtering with grep-v 
This challenge uses the `grep -v` command. 

### My solution 
**Flag** `pwn.college{MartNTEb80iTuUaRZ2Xqj7GUFEk.0FOxEzNxwSNxEzNzEzW}`
1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v "DECOY"
pwn.college{MartNTEb80iTuUaRZ2Xqj7GUFEk.0FOxEzNxwSNxEzNzEzW}
```

### What i learned 
1. While normal grep shows lines that match a pattern, `grep -v` shows lines that do NOT match a pattern.

# Dupliating piped data with tee
This challenge uses the `tee` command to duplicate data. 

### My solution 
**Flag** `pwn.college{U5-dfAh143EAtQAVcDhueIEmM4n.QXxITO0wSNxEzNzEzW}`
1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee secret | /challenge/college
Processing...
WARNING: you are overwriting file secret with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat secret
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "U5-dfAh1"
hacker@piping~duplicating-piped-data-with-tee:~$  /challenge/pwn --secret U5-dfAh1 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{U5-dfAh143EAtQAVcDhueIEmM4n.QXxITO0wSNxEzNzEzW}
```

### What i learned 
learned that the tee command duplicates data flowing through your pipes to any number of files provided on the command line.


## Process substitution for input 
uses the `diff` command to diff two sets of command outputs.

### my solution 
**Flag** `pwn.college{gYwFfu5LG241kqRTOL3HAUvR8eL.0lNwMDOxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
98a99
> pwn.college{gYwFfu5LG241kqRTOL3HAUvR8eL.0lNwMDOxwSNxEzNzEzW}
```

### What i learned 
Process substitution <(...) gives diff file like views of each command's output so we can compare them and extract the lines present only in the version that contains the real flag.


## writing to multiple programs 
this challenge uses process substitution for writing to commands.

### my solution
**flag** `pwn.college{YbA9V-Y0d7BdPR0vGAkfAYDx907.QXwgDN1wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
23469231237248478
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{YbA9V-Y0d7BdPR0vGAkfAYDx907.QXwgDN1wSNxEzNzEzW}
```

### What i learned
Used output process substitution >(command) with tee to send /challenge/hack’s output simultaneously to both /challenge/the and /challenge/planet.

## split-piping stderr and stdout 
This challenge required us to redirect stdout to one program and stderr to another.

### My solution 
**Flag** `pwn.college{8n6uTxh03EJ4X7L6pTx03pq5Fot.QXxQDM2wSNxEzNzEzW}`

I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{8n6uTxh03EJ4X7L6pTx03pq5Fot.QXxQDM2wSNxEzNzEzW}
```

### What i learned
Used output process substitution >(...) to hook the command’s stdout into /challenge/planet and its stderr (via 2>) into /challenge/the, keeping the streams separate.


# named pipes 
this challenge uses making our own named pipes calles `FIFOs`.

### My solution 
**Flag** `pwn.college{oalNRqhy_k1osuhKRkC0Dwtt_r6.01MzMDOxwSNxEzNzEzW}`

I connected the dojo host using SSH command.
```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@piping~named-pipes:~$ cat < /tmp/flag_fifo &
[1] 152
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{oalNRqhy_k1osuhKRkC0Dwtt_r6.01MzMDOxwSNxEzNzEzW}
[1]+  Done                    cat < /tmp/flag_fifo
```

### What i learned 
I learned that FIFO's will block any operations on them until both the read side of the pipe and the write side of the pipe are ready.

# 6. Shell variables

## Printing variables

### My solve

**Flag:** `pwn.college{QCFS19SuolOF42R8MjdY-qLdXd5.QX3UTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{QCFS19SuolOF42R8MjdY-qLdXd5.QX3UTN0wSNxEzNzEzW}
```

### What I learned

Using `echo` to print variables.

## Setting variables

In this challenge we need to assign variables some values.

### My solve

**Flag:** `pwn.college{o9CXGpR4y40ExwVjL0HViBwTUxH.QX5UTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~setting-variables:~$ echo $PWN
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
hacker@variables~setting-variables:~$ echo $PWN
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{o9CXGpR4y40ExwVjL0HViBwTUxH.QX5UTN0wSNxEzNzEzW}
```

### What I learned

1. We can assign values to variables just like other languages.
2. There are no spaces around the `=`. If we put spaces the shell won't recognize a variable assignment and will instead run the `VAR` command.

## Multi-word variables

This challenge uses quoting.

### My solve

**Flag:** `pwn.college{4kd9_HKZVel0_VMF3K4Vp6fYpZ1.QXwYTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~multi-word-variables:~$ echo $PWN

hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4kd9_HKZVel0_VMF3K4Vp6fYpZ1.QXwYTN0wSNxEzNzEzW}
```

### What I learned

1. How to set a variable's value to multiple terms.
2. Spaces have special significance in the shell, and there are places where we can't use them spuriously.

## Exploring variables

The goal of the challenge is to read the value of a specific variable and then pass that information to the challenge program.

### My solve

**Flag:** `pwn.college{UGRgjnqXacN1m_YmYFJJqQn8N30.QXyYTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~exporting-variables:~$ echo $PWN
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run PWN
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{UGRgjnqXacN1m_YmYFJJqQn8N30.QXyYTN0wSNxEzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

### What I learned

By default, variables that we set in a shell session are local to that shell process, which means other commands would not inherit them.

## Printing exported variables

This challenge requires the `env` command.

### My solution

**Flag:** `pwn.college{wDCRDeOwvgG0CmJ_VAj1R2zHRLH.QX4UTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=192a9bf50cc19a53d91b8e5008b7a4e75e803db0fdc6807c8a86556e838cdead
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{wDCRDeOwvgG0CmJ_VAj1R2zHRLH.QX4UTN0wSNxEzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

### What I learned

The `env` command prints out every exported variable set in your shell.

## Storing command output

This challenge uses the command substitution method.

### My solution

**Flag:** `pwn.college{UkLjBdm0XoXz4RIaBL3sttRixjL.QX1cDN1wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{UkLjBdm0XoXz4RIaBL3sttRixjL.QX1cDN1wSNxEzNzEzW}
```

### What I learned

I learned how to store the output of a command into a variable.

## Reading input

### My solution

**Flag:** `pwn.college{oMV_8hzH-Rk1ZTE1mLBdGcMA1QP.QX4cTN0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{oMV_8hzH-Rk1ZTE1mLBdGcMA1QP.QX4cTN0wSNxEzNzEzW}
```

### What I learned

The use of the `read` command to read input from the user.

## Reading files

This challenge uses the `read` command.

### My solution

**Flag:** `pwn.college{gJP2lM7qeVmwr0xFSKdAuV8O8bh.QXwIDO0wSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on [pwn.college](https://pwn.college/linux-luminarium/hello/) to complete the challenge.

```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gJP2lM7qeVmwr0xFSKdAuV8O8bh.QXwIDO0wSNxEzNzEzW}
```

### What I learned

The use of directly reading input from a file.

# 7. Data manupulation

## Translating characters

This challenge used the `tr` command to translate a string.

### My solve

**Flag:** `pwn.college{Ul0XhyMLDSg3DPskaGAQsqvTleM.01MxEzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on pwn.college to complete the challenge.

```bash
hacker@data~translating-characters:~$ /challenge/run | tr 'a-zA-Z' 'A-Za-z'
yOUR CASE-SWAPPED FLAG:
pwn.college{Ul0XhyMLDSg3DPskaGAQsqvTleM.01MxEzNxwSNxEzNzEzW}
```

### What I learned

1. `tr` translates the characters provided in its first argument to the characters provided in its second argument.
2. It translates characters it receives over standard input and prints them to standard output.

## Deleting characters

This challenge makes us delete particular parts of a command.

### My solve

**Flag:** `pwn.college{Ul0XhyMLDSg3DPskaGAQsqvTleM.01MxEzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on pwn.college to complete the challenge.

```bash
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p^%w^%n^.^c^ol%l^eg^%e^{%Q%0%g^%J%p%B%5%fEScd^%P^%w^61^%W^%oiK^%i^%b^S^%O^%B^%j^%_^.^0%F%N%x%Ez^%N^%x%w%S^N%x^E^z^%Nz^%E%z%W%}^%^%

hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{Q0gJpB5fEScdPw61WoiKibSOBj_.0FNxEzNxwSNxEzNzEzW}
```

### What I learned

1. `tr` can also be used to delete characters using the `-d` flag followed by the characters to delete.

## Deleting newlines

This challenge deletes newline characters.

### My solve

**Flag:** `pwn.college{4O9c0JYgSK39JWM_m7ROwkhD4b1.0VNxEzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on pwn.college to complete the challenge.

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{4O9c0JYgSK39JWM_m7ROwkhD4b1.0VN}
```

### What I learned

1. To represent a newline character in `tr`, we use `\n`.
2. Backslashes must be escaped when used inside quotes.

## Extracting the first few lines using head

This challenge uses the `head` command to display the first few lines of input.

### My solve

**Flag:** `pwn.college{QMrCKyEI-SKF1wdFwAFRqMN6jwG.0lNxEzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on pwn.college to complete the challenge.

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{QMrCKyEI-SKF1wdFwAFRqMN6jwG.0lNxEzNxwSNxEzNzEzW}
```

### What I learned

1. By default, `head` displays the first 10 lines.
2. The `-n` option allows us to specify how many lines to display.

## Extracting specific sections of text

This challenge uses the `cut` command to extract specific columns of data.

### My solve

**Flag:** `pwn.college{0AwnUjg7gOCzS-qx0eT42DxGmeR.01NxEzNxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on pwn.college to complete the challenge.

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f2 | tr -d '\n'
pwn.college{0AwnUjg7gOCzS-qx0eT42DxGmeR.01NxEzNxwSNxEzNzEzW}
```

### What I learned

1. The `-d` option specifies the delimiter between columns.
2. The `-f` option specifies which field (column) to extract.

## Sorting data

This challenge uses the `sort` command to order data.

### My solve

**Flag:** `pwn.college{4q_-gm98mBig7n3BT8k0yKv3yM_.0FM0MDOxwSNxEzNzEzW}`

1. I connected the dojo host using SSH command.

```bash
root@LAPTOP-IDCKVPOM:~# ssh  -i ./key hacker@dojo.pwn.college
```

2. Now the shell is connected to dojo. Now, I got the flag that I can submit on pwn.college to complete the challenge.

```bash
hacker@data~sorting-data:~$ cat /challenge/flags.txt | sort | tail -n 1
pwn.college{4q_-gm98mBig7n3BT8k0yKv3yM_.0FM0MDOxwSNxEzNzEzW}
```

### What I learned

1. By default, `sort` orders lines alphabetically.
2. Common options:

   * `-r`: reverse order
   * `-n`: numeric sort
   * `-u`: unique lines only
   * `-R`: random order



